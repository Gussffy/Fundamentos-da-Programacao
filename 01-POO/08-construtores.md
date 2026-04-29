# Construtores

## Introdução

Construtores são blocos de código especiais que inicializam objetos quando eles são instanciados. Em Java, um construtor tem o mesmo nome da classe e pode receber parâmetros necessários para garantir um estado inicial válido.

Motivação: garantir que objetos sejam criados em um estado consistente, evitando objetos parcialmente inicializados. Construtores também são ponto adequado para validar parâmetros obrigatórios e aplicar regras iniciais de negócio.

Erros comuns: ter construtores com muitos parâmetros (sinal de que a classe pode estar com responsabilidade excessiva), usar lógica complexa no construtor (torna testes mais difíceis) e esquecer de validar entradas. Em casos de construtores com muitos parâmetros, considere o pattern Builder.

## Objetivos

- Garantir estado inicial válido
- Simplificar a criação de objetos
- Reduzir erros de configuração manual

## Exemplo em Java

```java
public class Produto {
    private final String nome;
    private final double preco;

    public Produto(String nome, double preco) {
        if (nome == null || nome.isBlank()) {
            throw new IllegalArgumentException("Nome inválido");
        }
        if (preco < 0) {
            throw new IllegalArgumentException("Preço inválido");
        }
        this.nome = nome;
        this.preco = preco;
    }
}
```

## Quando usar

Sempre que a classe precisar receber dados obrigatórios no momento da criação.

## Boas práticas

- Valide os parâmetros
- Prefira campos `final` quando fizer sentido
- Evite construtores com muitos parâmetros; nesses casos, considere Builder

## Relacionados

- Encapsulamento
- Builder
- Modificadores de acesso

