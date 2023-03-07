# Análise de Dados Para Campanhas de Marketing Direto

Este repositório contém um projeto de análise de dados de campanhas de marketing direto de uma instituição bancária portuguesa. O objetivo da campanha é que o cliente faça a adesão do produto bancário: depósito a prazo.

O que é um depósito a prazo? 

Com um depósito a prazo, você guarda uma quantia de dinheiro por um período de tempo acordado (o 'prazo') - isso significa que você não pode acessar o dinheiro depositado até que o prazo termine. Em troca, você receberá uma taxa de juros garantida e proporcional ao prazo que selecionar.

## Objetivo do Projeto

O propósito deste tipo de projeto é fornecer insights sobre o desempenho das campanhas de marketing, com o objetivo de ajudar as empresas a entender como elas podem melhorar suas estratégias de marketing e, consequentemente, aumentar suas taxas de conversão.

O projeto foi desenvolvido utilizando a linguagem Python e várias bibliotecas de análise de dados, como Pandas, NumPy, Matplotlib e Seaborn.

Durante o projeto foi realizado as etapas de análise exploratória dos dados, tranformação de variáveis, identificação e tratamento de valores ausentes, análise univariada e multivariada.

Você encontra todo o passo a passo da análise no link: <a href="https://colab.research.google.com/drive/1kRSyRqks2J-FKqA552nSfBwOUOIYPzB-?usp=sharing">Análise de Dados Para Campanhas de Marketing Direto</a>.

Todas as decisões tomadas durante a análise estão documentadas abaixo, na seção **Relatório da Análise**.

## Objetivos da Aprendizagem 
* Desmembrar variáveis (colunas) com mais de uma informação?
* Definir e identificar valores ausentes;
* Decidir qual estratégia de tratamento de valores ausentes é mais a mais adequada para cada cenário;
* Categorização de variável numérica;
* Interpretação do histograma, box plot, média, mediana e moda;
* Análise univariada, bivariada e multivariada.

## Fonte dos Dados

Os dados para este projeto foram extraídos do <a href="https://archive.ics.uci.edu/ml/datasets/bank+marketing">Bank Marketing Data Set</a>, disponível no UCI Machine Learning Repository.

UCI Machine Learning Repository é um repositório de dados utilizado na área de aprendizado de máquina e mineração de dados. É mantido pela Universidade da Califórnia, em Irvine (UCI), e contém uma coleção de conjuntos de dados, bancos de dados, e ferramentas de software relacionadas ao aprendizado de máquina e mineração de dados. 

Utilizando o Excel, realizei diversas modificações nos dados, provocando problemas e valores ausentes, para que assim seja possível também trabalhar as técnicas de limpeza e tratamendo de dados.
Você pode encontrar facilmente o arquivo CSV modificado e utilizado neste projeto na pasta **dados**.

## Dicionário dos Dados

O arquivo CSV utilizado neste projeto possui **45.512 registros** de clientes bancários com **17 variáveis**, sendo **'y'** a variável resposta. Irei aqui fazer uma breve descrição das variáveis.

**job,age**: função, idade;

**education**: escolaridade;

**marital**: estado civil;

**default**: tem crédito em inadimplência?;

**balance**: saldo em conta;

**housing**: possui crédito em habitação?;

**loan**: tem empréstimo pessoal?;

**contact**: tipo de comunicação de contato;

**day**: último dia de contato do mês;

**month**: último mês de contato do ano;

**duration**: duração do ultimo contato;

**campaign**: número de contatos realizados durante esta campanha e para este cliente;

**pdays**: número de dias que se passaram desde que o cliente foi contatado pela última vez em uma campanha anterior (numérico, -1 significa que o cliente não foi contatado anteriormente);

**previous**: número de contatos realizados antes desta campanha e para este cliente;

**poutcome**: resultado da campanha de marketing anterior ("desconhecido","outro","fracasso","sucesso");

**y**: O cliente adquiriu o produto (depósito a prazo) nesta campanha?.

## Relatório da Análise

A tabela em análise, possui originalmente 45211 registros de ligações para clientes bancários contendo 17 variáveis, conforme descrito no dicionário de dados. 

No início da análise exploratória dos dados foi possível identificar que a coluna **'job,age'** agrupava duas informações, foi necessário então **desmembrar** a coluna para facilitar a análise;

### Tratamento de Valores Ausentes 

Uma abordagem comum para tratar valores ausentes é utilizar medidas de tendência central para preencher os valores ausentes. As medidas de tendência central incluem a média, a mediana e a moda. Iremos utilizá-las nessa etapa do projeto.

A nova coluna 'age', possuia 15 valores ausentes(nan), além de 10 valores de idade iguais a 0. Entendendo que não existe cliente bancário com idade igual a 0, estes valores também foram identificados como valores ausentes.

Segue abaixo as técnicas utilizadas para o tratar os valores ausentes, é importante salientar que não existe estratégia ideal, devemos analisar cada cenário e tentar gerar o menor impacto possível nos dados.

* O percentual de valores ausentes da coluna **'age'** era muito baixo, em torno de 0,06%. Analisando o histograma, o boxplot, a media, a moda e a mediana desta variável foi possivel perceber uma assimetria nos dados e diversos valores outliers, sendo assim a média não deve ser usada como estratégia para preenchimento dos valores ausentes da coluna 'age'. Alem disso, a moda(32) é um valor muito abaixo da media(41) e da mediana(39). Se imputar a moda, estaria reforçando essa informação. Portanto, os valores ausentes da variável 'age' foram preenchidos pela **mediana(39)**.

* Na a coluna **'month'**, que representa o mês do contato com o cliente, possuia 40 valores ausentes, representando um percentual de 0,09%. A variável 'month' é do tipo categórica, portanto tomei a decisão de preencher seus valores ausentes com a **moda(may)**.

* A coluna **'y'** indica se o cliente aderiu ou não ao produto bancário oferecido. A percentual de valores ausentes nessa coluna é de 0,04%, ou seja, um valor baixo. No entanto, quando se trata de valores ausentes na variável alvo, a imputação não é adequada, pois pode introduzir um viés nos resultados da análise. Isso ocorre porque a imputação pressupõe que os dados ausentes são aleatórios e não relacionados com outras variáveis, o que pode não ser verdadeiro para a variável alvo. Portanto, neste caso, foi **delatado os registros** que possuem valor ausente na variável 'y'.

* O dicionário de dados informa que na variável **'pdays'**, -1 indica valores ausentes. Nesta coluna temos então 82% de valores ausentes, portanto foi feito a **deleção da coluna**.

### Análise Univariada

**1- Qual a proporção de ligações por faixa etária do cliente?**

Para responder essa pergunta foi preciso primeiramente criar uma nova coluna para classificar o cliente por faixa etária. Como as idades do cliente mais novo e do cliente mais velho são 18 e 95, respectivamente, foi possível fazer uma divisão igualitária das idades para cada 6 anos. Segue abaixo o gráfico de barras que responde essa pergunta.

![Faixa Etária](https://raw.githubusercontent.com/raulrosapacheco/Campanhas-Telemarketing-Financeiras/main/imagens/faixa-etaria.png)

**2 - Qual a proporção de ligações por nível de escolaridade?**








