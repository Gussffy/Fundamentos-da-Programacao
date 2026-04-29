# Composição vs Herança

## Introdução

Composição e herança são duas formas de relacionar classes: herança modela uma relação de especialização ("é um"), enquanto composição modela uma relação de "tem um" ou uso, em que um objeto contém ou usa outro como parte de seu funcionamento.

Motivação: preferir composição quando se busca flexibilidade e baixo acoplamento, já que componentes podem ser trocados em tempo de execução; usar herança quando houver uma relação clara e estável de tipo entre as classes.

Erros comuns: usar herança apenas para reaproveitar código (sem relação semântica), o que cria hierarquias frágeis; ou aplicar composição de forma excessiva sem considerar clareza do modelo. Um bom design equilibra ambos quando apropriado.

## Objetivos

- Entender quando usar cada abordagem
- Evitar hierarquias profundas demais
- Preferir flexibilidade no design

## Exemplo em Java

### Composição

```java
public class Motor {
    public void ligar() {
        System.out.println("Motor ligado");
    }
}

public class Carro {
    private final Motor motor;

    public Carro(Motor motor) {
        this.motor = motor;
    }

    public void ligar() {
        motor.ligar();
        System.out.println("Carro pronto para uso");
    }
}
```

### Herança

```java
public class Veiculo {
    public void mover() {
        System.out.println("Veículo em movimento");
    }
}

public class Bicicleta extends Veiculo {
    @Override
    public void mover() {
        System.out.println("Bicicleta sendo pedalada");
    }
}
```

## Regra prática

Se a relação for "tem um", prefira composição. Se for "é um", herança pode fazer sentido.

## Relacionados

- Encapsulamento
- Herança
- Polimorfismo

