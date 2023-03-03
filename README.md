# Análise de Dados Para Campanhas de Marketing Direto

Este repositório contém um projeto de análise de dados de campanhas de marketing direto de instituição bancária portuguesa. 

O objetivo do projeto é fornecer insights sobre o desempenho das campanhas de marketing direto realizadas por instituições financeiras, com o objetivo de ajudar as empresas a entender como elas podem melhorar suas estratégias de marketing e, consequentemente, aumentar suas taxas de conversão.

O projeto foi desenvolvido utilizando a linguagem Python e várias bibliotecas de análise de dados, como Pandas, NumPy, Matplotlib e Seaborn.

## Fonte dos Dados

Os dados para este projeto foram extraídos do <a href="https://archive.ics.uci.edu/ml/datasets/bank+marketing">Bank Marketing Data Set</a>, disponível no UCI Machine Learning Repository.

UCI Machine Learning Repository é um repositório de dados utilizado na área de aprendizado de máquina e mineração de dados. É mantido pela Universidade da Califórnia, em Irvine (UCI), e contém uma coleção de conjuntos de dados, bancos de dados, e ferramentas de software relacionadas ao aprendizado de máquina e mineração de dados. 

Utilizando o Excel, realizei diversas modificações nos dados, provocando problemas e valores ausentes, para que assim seja possível também trabalhar as técnicas de limpeza e tratamendo de dados.
Você pode encontrar facilmente o arquivo CSV modificado e utilizado neste projeto na pasta **dados**.

## Dicionário dos Dados

O arquivo CSV utilizado neste projeto possui **45.512 registros** com **17 variáveis**, sendo **'y'** a variável resposta ou variável alvo. Irei aqui fazer uma breve descrição das variáveis.

**job,age**: função, idade;

**education**: escolaridade;

**marital**: estado civil;

**default**: tem crédito em inadimplência?;

**balance**: saldo em conta;

**housing**: possui crédito habitação?;

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



