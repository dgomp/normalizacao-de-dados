# Normalização de Dados
Resumo sobre Normalização de Dados.


## O que é?

A normalização de dados é um processo que tem como objetivo evitar problemas na inclusão, exclusão e alteração de registros.

O processo de normalização aplica uma série de regras sobre as tabelas de um banco de dados, para verificar se estas estão corretamente projetadas. As formas normais são importantes instrumentos para resolver antecipadamente problemas na estrutura do banco de dados. Na prática, usamos um conjunto de três Formas Normais:

* Primeira Forma Normal (1FN);
* Segunda Forma Normal (2FN)
* Terceira Forma Normal (3FN).


### Primeira Forma Normal (1FN)

Estabelece que cada coluna de uma tabela deve ter valores atômicos, ou seja, não deve haver valores múltiplos ou compostos em uma única coluna.

### Segunda Forma Normal (2FN)

Estabelece que cada coluna de uma tabela deve depender da chave primária da tabela, e não de uma chave parcial.


### Terceira Forma Normal (3FN)

Estabelece que cada coluna de uma tabela deve depender apenas da chave primária da tabela, e não de outras colunas.


## Vantagens

As principais vantagens da normalização de dados são: redução da redundância de dados, agrupamento lógico dos dados, assegura a integridade referencial nos dados, melhora a precisão, bem como o desempenho.


## Desvantagens

Já como desvantagens, temos uma maior complexidade do modelo de dados, bem como maior tempo para desenvovolver e maior número de tabelas.


Fonte: [Blog do Zouza](https://medium.com/blog-do-zouza/modelagem-relacional-uma-visão-geral-44cd8807fc87), [eHow](https://www.ehow.com.br/interferencia-retroativa-proativa-fatos_61464/) e [Acervo Lima](https://acervolima.com/o-que-e-normalizacao-de-dados/).
