# Guia de Conteúdo

> Um resumo explicativo dos principais tópicos que serão estudados na disciplina, para te dar uma base antes das aulas começarem.

---

## 1. O que é Machine Learning?

Machine Learning (Aprendizado de Máquina) é a área da Inteligência Artificial em que, em vez de **programar regras explícitas** para resolver um problema, você fornece **dados** para um algoritmo, e ele **aprende os padrões sozinho**.

Exemplo clássico: para identificar se um e-mail é spam, você não escreve manualmente centenas de regras ("se contém a palavra 'grátis' então é spam"). Em vez disso, você mostra milhares de e-mails já classificados como spam/não-spam, e o modelo aprende a reconhecer os padrões que definem um spam.

De forma resumida, todo problema de ML segue essa lógica:

```
Dados de entrada → Algoritmo de aprendizado → Modelo treinado → Previsões sobre dados novos
```

Os três grandes paradigmas de aprendizado que você vai estudar são: **supervisionado**, **não supervisionado** e **por reforço**. Entender a diferença entre eles é a base de tudo o que vem depois.

---

## 2. Aprendizado Supervisionado

É o tipo mais comum e o ponto de partida da disciplina. O modelo aprende a partir de um conjunto de dados **rotulado** — ou seja, para cada exemplo de entrada, você já sabe qual é a resposta certa (o "gabarito").

**Analogia:** é como estudar para uma prova com uma lista de exercícios que já vêm com o gabarito. Você aprende o padrão comparando sua tentativa com a resposta certa, e ajusta seu raciocínio.

Dentro do aprendizado supervisionado existem duas grandes tarefas:

### 2.1 Regressão

Usada quando a resposta que você quer prever é um **valor numérico contínuo**.

- Exemplos: prever o preço de um imóvel, prever a temperatura de amanhã, prever quanto uma empresa vai vender no próximo mês.
- Algoritmo mais básico: **Regressão Linear** — encontra a melhor reta (ou hiperplano) que relaciona as variáveis de entrada com a saída numérica.

### 2.2 Classificação

Usada quando a resposta é uma **categoria discreta**.

- Exemplos: spam ou não-spam, doente ou saudável, aprovado ou reprovado, qual raça de cachorro é essa foto.
- Algoritmos comuns: **Regressão Logística**, **Árvores de Decisão**, **KNN (K-Nearest Neighbors)**, **SVM (Support Vector Machines)**.

**Dica mental:** número → regressão; categoria/rótulo → classificação.

---

## 3. Aprendizado Não Supervisionado

Aqui os dados **não têm rótulo** — não existe resposta certa fornecida. O algoritmo precisa encontrar **estrutura e padrões escondidos** nos dados sozinho.

**Analogia:** é como receber uma caixa de fotos misturadas, sem legendas, e ter que organizá-las em grupos por conta própria, com base em semelhanças visuais.

Principal tarefa que você vai ver:

### 3.1 Clusterização (Agrupamento)

Agrupar dados semelhantes entre si em "clusters" (grupos), sem saber de antemão quais são esses grupos.

- Exemplos: segmentação de clientes por comportamento de compra, agrupamento de notícias por assunto, identificação de perfis de usuários.
- Algoritmo clássico: **K-Means** — divide os dados em K grupos, minimizando a distância entre cada ponto e o centro do seu grupo.

Outras aplicações do não supervisionado incluem **redução de dimensionalidade** (simplificar dados com muitas variáveis, mantendo a informação relevante) e **detecção de anomalias** (encontrar dados fora do padrão, como fraudes).

---

## 4. Aprendizado por Reforço

Um paradigma bem diferente dos dois anteriores. Aqui não existe um conjunto de dados rotulado — existe um **agente** que interage com um **ambiente**, toma **ações**, e recebe **recompensas** ou **punições** dependendo do resultado dessas ações. Com o tempo, o agente aprende qual estratégia (chamada de **política**) maximiza a recompensa acumulada.

**Analogia:** é como treinar um cachorro. Você não dá uma lista de regras — você recompensa comportamentos bons (petisco) e desencoraja comportamentos ruins, e com repetição o cachorro aprende a melhor "política" de comportamento.

- Exemplos: IAs que jogam xadrez/Go/videogames, robôs que aprendem a andar, carros autônomos, sistemas de recomendação que se adaptam ao comportamento do usuário em tempo real.
- Conceitos-chave: **agente**, **ambiente**, **estado**, **ação**, **recompensa**, **política**.

---

## 5. Exploração e Generalização

Dois conceitos transversais, que aparecem em praticamente todo o curso:

### 5.1 Generalização

A capacidade do modelo de funcionar bem em **dados novos**, que ele nunca viu durante o treino — e não só nos dados de treino. Dois problemas opostos podem acontecer:

- **Overfitting** — o modelo "decora" os dados de treino (inclusive o ruído), e performa mal em dados novos. É como decorar as respostas de uma prova específica sem entender a matéria: funciona só naquela prova.
- **Underfitting** — o modelo é simples demais para captar os padrões reais dos dados, e performa mal em tudo, inclusive no treino.

O equilíbrio ideal entre esses dois extremos é um dos maiores desafios práticos em ML.

### 5.2 Exploração (Exploration vs. Exploitation)

Conceito mais associado ao aprendizado por reforço: o agente precisa decidir entre **explorar** (tentar ações novas, que podem revelar estratégias melhores) e **exploitar** (usar a ação que já sabe que dá bons resultados). Focar demais em um dos dois lados prejudica o aprendizado — exploração demais nunca consolida uma boa estratégia; exploitação demais pode travar o agente em uma solução não-ótima.

---

## 6. Introdução ao Ambiente de Desenvolvimento

Parte prática da disciplina, onde você vai configurar e usar as ferramentas padrão de mercado para ML em Python:

- **Python** — linguagem principal usada em ML por sua simplicidade e ecossistema de bibliotecas.
- **Jupyter Notebook** — ambiente interativo muito usado para experimentação e visualização de dados.
- **NumPy** — operações numéricas e vetoriais eficientes.
- **Pandas** — manipulação e limpeza de dados tabulares (DataFrames).
- **Scikit-learn** — biblioteca com implementações prontas dos principais algoritmos de ML (regressão, classificação, clusterização), muito usada para aprender e prototipar.
- **Matplotlib / Seaborn** — visualização de dados e resultados.

Vale a pena já se familiarizar com o básico de pandas (leitura de dados, filtragem, tratamento de valores ausentes) e com a lógica geral do scikit-learn (`fit`, `predict`, `score`), pois isso é praticamente universal em qualquer projeto de ML.

---

## 7. Algoritmos de ML (Regressão, Classificação e Clusterização)

Bloco onde a teoria vira prática, aprofundando os algoritmos específicos de cada tarefa:

|Tarefa|Algoritmos comuns|Ideia central|
|---|---|---|
|Regressão|Regressão Linear, Regressão Polinomial|Ajustar uma função contínua aos dados|
|Classificação|Regressão Logística, KNN, Árvore de Decisão, SVM|Separar os dados em classes/categorias|
|Clusterização|K-Means, Clusterização Hierárquica|Agrupar dados por similaridade, sem rótulos|

Um ponto importante que costuma aparecer aqui: como **avaliar** se um modelo é bom (ex: acurácia, precisão, recall para classificação; erro médio para regressão), mesmo sem entrar no mérito de provas — é conhecimento técnico central da disciplina.

---

## 8. Aplicação dos Algoritmos de ML

Etapa de consolidação: pegar os algoritmos estudados e aplicá-los a um problema prático e realista, do início ao fim — desde a coleta/tratamento dos dados, passando pela escolha e treino do modelo, até a interpretação dos resultados.

Esse é o momento em que os conceitos de generalização (item 5) se tornam muito concretos: um modelo que parece perfeito nos dados de treino, mas falha completamente em dados novos, é um erro comum nessa etapa — e é exatamente o tipo de armadilha que a disciplina busca ensinar a evitar.

---

## 9. Resumo Visual dos Paradigmas

|Paradigma|Tem rótulo?|Objetivo|Exemplo|
|---|---|---|---|
|Supervisionado|Sim|Prever valor/categoria|Prever preço de casa, detectar spam|
|Não supervisionado|Não|Encontrar padrões/agrupar|Segmentar clientes|
|Por reforço|Não (recompensa)|Maximizar recompensa acumulada|Jogo de xadrez, robô autônomo|

---

## 10. Glossário Rápido

- **Modelo** — a representação matemática que o algoritmo constrói a partir dos dados de treino.
- **Feature (característica/variável)** — cada informação de entrada usada para prever algo (ex: metragem e localização de um imóvel).
- **Label (rótulo)** — a resposta certa associada a um exemplo, no aprendizado supervisionado.
- **Treino/Teste (train/test split)** — prática de separar os dados em um conjunto para treinar o modelo e outro para testar sua generalização.
- **Overfitting / Underfitting** — ver seção 5.1.
- **Hiperparâmetro** — configuração do algoritmo definida antes do treino (ex: número de clusters no K-Means), diferente dos parâmetros que o próprio modelo aprende.