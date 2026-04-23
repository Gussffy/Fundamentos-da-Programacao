# Princípios SOLID

Aqui vai a minha explicação sobre os princípios SOLID, com exemplos em Java e Spring Boot para ilustrar cada um deles.

Os princípios SOLID são um conjunto de boas práticas de programação que ajudam no desenvolvimento de software com código mais compreensível, flexível e fácil de manter. Esses princípios foram definidos por Robert C. Martin (Uncle Bob). Neste arquivo, exploraremos cada um dos princípios com exemplos em Java e Spring Boot.

## 1. Single Responsibility Principle (SRP)
**Princípio da Responsabilidade Única:** Uma classe deve ter um, e apenas um, motivo para mudar. Em outras palavras, cada classe deve ter apenas uma responsabilidade.

### Exemplo:
```java
// Classe que segue o SRP
public class EmailService {
    public void sendEmail(String recipient, String message) {
        // Código para enviar email
    }
}
```
```java
public class UserService {
    private final EmailService emailService;

    public UserService(EmailService emailService) {
        this.emailService = emailService;
    }

    public void registerUser(String username, String email) {
        // Lógica de registro do usuário
        emailService.sendEmail(email, "Bem-vindo!");
    }
}
```
Aqui, `EmailService` é responsável apenas por enviar e-mails, enquanto `UserService` cuida do registro do usuário.

---

## 2. Open/Closed Principle (OCP)
**Princípio Aberto/Fechado:** Classes, módulos e funções devem ser abertos para extensão, mas fechados para modificação.

### Exemplo em Spring Boot com Strategy Pattern:
```java
public interface PaymentMethod {
    void pay(double amount);
}

public class CreditCardPayment implements PaymentMethod {
    @Override
    public void pay(double amount) {
        System.out.println("Pagando com cartão de crédito: " + amount);
    }
}
```

```Java
public class PayPalPayment implements PaymentMethod {
    @Override
    public void pay(double amount) {
        System.out.println("Pagando com PayPal: " + amount);
    }
}
```
```java
@Service
public class PaymentService {
    public void processPayment(PaymentMethod paymentMethod, double amount) {
        paymentMethod.pay(amount);
    }
}
```
Você pode facilmente adicionar novas formas de pagamento sem modificar `PaymentService`.

---

## 3. Liskov Substitution Principle (LSP)
**Princípio da Substituição de Liskov:** Objetos de uma classe derivada devem ser substituíveis por objetos da classe base sem alterar a correção do programa.

### Exemplo:
```java
public class Rectangle {
    private int width;
    private int height;

    public int getWidth() {
        return width;
    }

    public void setWidth(int width) {
        this.width = width;
    }

    public int getHeight() {
        return height;
    }

    public void setHeight(int height) {
        this.height = height;
    }

    public int getArea() {
        return width * height;
    }
}
```

```java
public class Square extends Rectangle {
    @Override
    public void setWidth(int width) {
        super.setWidth(width);
        super.setHeight(width);
    }

    @Override
    public void setHeight(int height) {
        super.setWidth(height);
        super.setHeight(height);
    }
}

// Uso correto
Rectangle rect = new Rectangle();
rect.setWidth(5);
rect.setHeight(10);

Rectangle square = new Square();
square.setWidth(5);
```
Subclasses como `Square` devem se comportar de maneira consistente com a classe base `Rectangle`.

---

## 4. Interface Segregation Principle (ISP)
**Princípio da Segregação de Interfaces:** Uma classe não deve ser forçada a depender de interfaces que não utiliza.

### Exemplo:
```java
public interface Printer {
    void print(Document document);
}

public interface Scanner {
    void scan(Document document);
}
```
```java
public class MultiFunctionPrinter implements Printer, Scanner {
    @Override
    public void print(Document document) {
        System.out.println("Imprimindo: " + document.getContent());
    }

    @Override
    public void scan(Document document) {
        System.out.println("Escaneando: " + document.getContent());
    }
}
```
```java
public class SimplePrinter implements Printer {
    @Override
    public void print(Document document) {
        System.out.println("Imprimindo: " + document.getContent());
    }
}
```
Aqui, `SimplePrinter` não é forçada a implementar métodos de `Scanner` que não utiliza.

---

## 5. Dependency Inversion Principle (DIP)
**Princípio da Inversão de Dependência:** Dependa de abstrações, não de implementações concretas.

### Exemplo em Spring Boot:
```java
public interface MessageSender {
    void sendMessage(String message);
}
```
```java
@Service
public class EmailSender implements MessageSender {
    @Override
    public void sendMessage(String message) {
        System.out.println("Enviando e-mail: " + message);
    }
}
```
```java
@Service
public class NotificationService {
    private final MessageSender messageSender;

    public NotificationService(MessageSender messageSender) {
        this.messageSender = messageSender;
    }

    public void notify(String message) {
        messageSender.sendMessage(message);
    }
}
```
Com o DIP, o `NotificationService` depende da abstração `MessageSender`, permitindo substituir `EmailSender` por outra implementação facilmente.

---

Esses cinco princípios ajudam a criar sistemas mais manuteníveis, flexíveis e robustos. Ao aplicá-los, você terá um software bem estruturado e preparado para evoluir com as mudanças ao longo do tempo.