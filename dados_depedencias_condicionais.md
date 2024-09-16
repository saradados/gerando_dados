** O que são Dados com Dependências Condicionais?**

### Visão Geral
Os **dados com dependências condicionais** referem-se a conjuntos de dados em que o relacionamento entre variáveis depende do valor de uma ou mais outras variáveis. Esse conceito é amplamente utilizado em probabilidade, estatística e aprendizado de máquina, especialmente em modelos como redes bayesianas e árvores de decisão. 

Dependências condicionais ajudam a capturar a estrutura interna de um conjunto de dados, permitindo modelar como uma variável depende de outra, dadas certas condições ou evidências.

### Dependência Condicional na Estatística

A dependência condicional ocorre quando duas variáveis são **independentes**, exceto quando uma terceira variável (ou conjunto de variáveis) é conhecida. Em termos probabilísticos, duas variáveis \( X \) e \( Y \) são condicionalmente dependentes dado \( Z \) se o valor de \( Z \) influencia a relação entre \( X \) e \( Y \). Formalmente:

\[
P(X, Y | Z) diferente P(X | Z) P(Y | Z)
\]

Se \( X \) e \( Y \) forem **condicionalmente independentes** dado \( Z \), a probabilidade conjunta de \( X \) e \( Y \) é simplesmente o produto das probabilidades condicionais de cada uma:

\[
P(X, Y | Z) = P(X | Z) P(Y | Z)
\]

### Exemplo de Dependência Condicional

Imagine o cenário de análise de saúde, onde você deseja modelar a probabilidade de uma pessoa ter uma doença com base em dados de sintomas e idade.

- **Variável \( X \)**: Doença (sim/não)
- **Variável \( Y \)**: Sintomas (por exemplo, febre)
- **Variável \( Z \)**: Idade

A dependência condicional entra em cena quando consideramos que a relação entre a doença e os sintomas pode variar dependendo da idade. Ou seja, a probabilidade de uma pessoa ter uma doença dada a presença de sintomas pode mudar conforme a faixa etária.

### Aplicações de Dependências Condicionais

1. **Redes Bayesianas**
    - Um modelo probabilístico que representa um conjunto de variáveis e suas dependências condicionais usando um grafo acíclico direcionado.
    - Exemplo: Uma rede bayesiana pode modelar a probabilidade de doenças com base em variáveis como idade, sexo e histórico familiar, capturando dependências condicionais entre elas.

2. **Árvores de Decisão**
    - Modelos de aprendizado de máquina que utilizam dependências condicionais para dividir os dados com base em diferentes variáveis, criando ramos e nós que representam como cada variável depende das demais.
    - Exemplo: Uma árvore de decisão pode usar idade, ocupação e renda para prever a probabilidade de uma pessoa comprar um carro, considerando a dependência entre essas variáveis.

### Como Identificar Dependências Condicionais

1. **Teste de Independência Condicional**
    - Para verificar se duas variáveis são condicionalmente independentes, pode-se aplicar testes estatísticos como o teste de **qui-quadrado** ou o teste de **Fisher**.
  
2. **Modelos Gráficos Probabilísticos**
    - Redes bayesianas ou modelos gráficos probabilísticos representam dependências condicionais entre variáveis de maneira visual. Cada nó do grafo representa uma variável, e as arestas representam dependências condicionais.

### Exemplo de Dados com Dependências Condicionais

Aqui está um exemplo simples que ilustra dependências condicionais em um conjunto de dados de candidatos a emprego:

```csv
idade,experiencia,educacao,contratado
25,2,graduação,não
30,5,pós-graduação,sim
22,1,graduação,não
35,10,médio,sim
28,3,graduação,sim
```

Neste exemplo:
- A probabilidade de um candidato ser contratado depende da experiência e da educação, mas pode ser influenciada pela idade.
- A variável "idade" pode condicionar o efeito de "educação" na contratação.

### Como Analisar Dependências Condicionais

1. **Bibliotecas de Programação**:
    - Em **Python**, bibliotecas como `pgmpy` e `bnlearn` permitem modelar e analisar dependências condicionais usando redes bayesianas.
    - Exemplo de criação de uma rede bayesiana com dependências condicionais usando `pgmpy`:
      ```python
      from pgmpy.models import BayesianNetwork
      from pgmpy.factors.discrete import TabularCPD

      # Definindo a estrutura do grafo (rede bayesiana)
      model = BayesianNetwork([('idade', 'contratado'),
                               ('experiencia', 'contratado'),
                               ('educacao', 'contratado')])

      # Definindo as distribuições condicionais (CPDs)
      cpd_idade = TabularCPD(variable='idade', variable_card=3, values=[[0.3], [0.4], [0.3]])
      cpd_experiencia = TabularCPD(variable='experiencia', variable_card=3, values=[[0.2], [0.5], [0.3]])
      cpd_educacao = TabularCPD(variable='educacao', variable_card=3, values=[[0.4], [0.4], [0.2]])
      cpd_contratado = TabularCPD(variable='contratado', variable_card=2,
                                  values=[[0.9, 0.7, 0.6, 0.8, 0.5, 0.4, 0.7, 0.6, 0.4],
                                          [0.1, 0.3, 0.4, 0.2, 0.5, 0.6, 0.3, 0.4, 0.6]],
                                  evidence=['idade', 'experiencia', 'educacao'],
                                  evidence_card=[3, 3, 3])

      model.add_cpds(cpd_idade, cpd_experiencia, cpd_educacao, cpd_contratado)

      # Checando se a rede está válida
      print(model.check_model())
      ```

2. **Ferramentas de Visualização**:
    - Gráficos como árvores de decisão ou redes bayesianas podem ser úteis para visualizar as dependências condicionais entre variáveis. Ferramentas como **Power BI**, **Tableau** ou **Gephi** podem ajudar na visualização gráfica dessas relações.

### Benefícios de Modelar Dependências Condicionais

1. **Melhoria na Precisão dos Modelos**
    - Capturar as dependências condicionais entre variáveis pode melhorar a precisão de previsões em modelos de aprendizado de máquina e estatísticos.
  
2. **Redução de Complexidade**
    - Ao modelar dependências condicionais, pode-se simplificar a análise de dados, focando apenas nas variáveis que realmente influenciam outras, dado um determinado contexto.

### Como Usar este Repositório

1. Clone o repositório para acessar exemplos de dados com dependências condicionais.
2. Utilize bibliotecas de aprendizado de máquina ou estatística para explorar as dependências condicionais nos dados.
3. Teste diferentes abordagens para modelagem e análise desses dados, como redes bayesianas ou árvores de decisão.

### Contribuições

Envie um **pull request** para sugerir novas formas de modelar e analisar dependências condicionais ou adicionar exemplos adicionais de dados com essa característica.

---


