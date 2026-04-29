# `equals`, `hashCode` e `toString`

## Introdução

Os métodos `equals`, `hashCode` e `toString` são fundamentais para a interoperabilidade dos objetos em coleções, para comparações por valor e para gerar saídas legíveis durante depuração e logging.

Motivação: implementar corretamente `equals` e `hashCode` garante que objetos possam ser usados em `HashSet`, `HashMap` e outras estruturas que dependem de igualdade e hashing. `toString` fornece uma representação textual útil para logs e debugging.

Erros comuns: definir `equals` sem atualizar `hashCode` (quebrando contratos), basear igualdade em campos mutáveis sem cuidado, ou gerar `toString` com informações sensíveis. Use `Objects.equals` e `Objects.hash` para reduzir erros e prefira campos estáveis como base de igualdade.

## Objetivos

- Comparar objetos por valor
- Garantir comportamento correto em `HashSet` e `HashMap`
- Melhorar a depuração com `toString`

## Exemplo em Java

```java
import java.util.Objects;

public class Usuario {
    private final Long id;
    private final String nome;

    public Usuario(Long id, String nome) {
        this.id = id;
        this.nome = nome;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Usuario usuario = (Usuario) o;
        return Objects.equals(id, usuario.id);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id);
    }

    @Override
    public String toString() {
        return "Usuario{id=" + id + ", nome='" + nome + "'}";
    }
}
```

## Quando usar

Sempre que objetos precisarem ser comparados ou exibidos de forma útil.

## Boas práticas

- Baseie `equals` e `hashCode` nos mesmos campos
- Evite usar campos mutáveis sem necessidade

## Relacionados

- Encapsulamento
- Coleções

