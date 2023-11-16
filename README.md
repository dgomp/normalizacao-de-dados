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

* Exemplo:

    |  ID |  Nome Completo |  Nascimento  |    Telefone   |
    | :-: | :------------: | :----------: | :-----------: |
    | `1` | `SILVA, Jose`  | `08/15/1985` | `85913255698` |
    | `1` | `SILVA, Jose`  | `08/15/1985` | `85912345698` |
    | `2` | `LOPES, Maria` | `01/03/1972` | `85913311254` |

    > *A mesma pessoa aparece duas vezes, pois possui dois telefones.*

    Para resolver esse problema, teremos que dividir a tabela em **duas**.

    1. Somente ID, Nome e Data de Nascimento:

        |  ID |  Nome Completo |  Nascimento  |
        | :-: | :------------: | :----------: |
        | `1` | `SILVA, Jose`  | `08/15/1985` |
        | `2` | `LOPES, Maria` | `01/03/1972` |

        > *Tabela sem a coluna de telefone.*

    2. ID e Telefone:

        |  ID |   Telefone   |
        | :-: | :----------: |
        | `1` | `85913255698`|
        | `1` | `85912345698`|
        | `2` | `85913311254`|

        > *Tabela somente com ID e telefone.*

Agora, não teremos informações repetidas na tabela.


### Segunda Forma Normal (2FN)

Estabelece que cada coluna de uma tabela deve depender da chave primária da tabela, e não de uma chave parcial.

* Exemplo:

    |  IDVenda |    DtVenda   | CodCli | CodLivro | CodAutor | CodEditora | Quantidade |  VlrUnd |
    | :------: | :----------: | :----: | :------: | :------: | :--------: | :--------: | :-----: |
    |    `1`   | `03/29/2023` |   `1`  |    `1`   |   `38`   |    `10`    |    `11`    | `54.10` |
    |    `2`   | `04/31/2023` |   `2`  |    `2`   |   `54`   |    `10`    |    `22`    | `95.30` |
    |    `3`   | `07/01/2023` |   `2`  |    `3`   |   `54`   |    `10`    |    `33`    | `84.70` |

    > *Aparece código do livro, código do autor e código da editora.*

  Para resolver esse problema, teremos que dividir a tabela em **duas**.

    1. Somente IDVenda, DtVenda, CodCli, CodLivro, Quantidade e VlrUnd:

        |  IDVenda |    DtVenda   | CodCli | CodLivro | Quantidade |  VlrUnd |
        | :------: | :----------: | :----: | :------: | :--------: | :-----: |
        |    `1`   | `03/29/2023` |   `1`  |    `1`   |    `11`    | `54.10` |
        |    `2`   | `04/31/2023` |   `2`  |    `2`   |    `22`    | `95.30` |
        |    `3`   | `07/01/2023` |   `2`  |    `3`   |    `33`    | `84.70` |

        > *Primeira tabela sem as colunas CodAutor e CodEditora.*

    2. CodLivro, CodAutor e CodEditora:

        | CodLivro | CodAutor | CodEditora |
        | :------: | :------: | :--------: |
        |    `1`   |   `38`   |    `10`    |
        |    `2`   |   `54`   |    `10`    |
        |    `3`   |   `54`   |    `10`    |

        > *Segunda tabela somente com CodLivro, CodAutor e CodEditora.*

Agora, apenas o CodLivro será suficiente, na primeira coluna, para já puxar o CodAutor e o CodEditora.


### Terceira Forma Normal (3FN)

Estabelece que cada coluna de uma tabela deve depender apenas da chave primária da tabela, e não de outras colunas.

* Exemplo:

    |  CodEditora |   NomeEdit   |  Endereco | CodTransp |   Transp   |
    | :---------: | :----------: | :-------: | :-------: | :--------: |
    |     `1`     |    `Atlas`   |   `2005`  |    `1`    | `Transp 1` |
    |     `2`     | `Intrínseca` |   `2005`  |    `2`    | `Transp 2` |
    |     `3`     |   `Saraiva`  |   `2005`  |    `3`    | `Transp 3` |

    > *Aparece código da transportadora e o nome da transportadora.*

  Isso é visto como informação desnecesária. Para resolver esse problema, teremos que dividir a tabela em **duas**.


    1. Somente CodEditora, NomeEdit, Endereco, CodTransp:

        |  CodEditora |   NomeEdit   |  Endereco | CodTransp |
        | :---------: | :----------: | :-------: | :-------: |
        |     `1`     |    `Atlas`   |   `2005`  |    `1`    |
        |     `2`     | `Intrínseca` |   `2005`  |    `2`    |
        |     `3`     |   `Saraiva`  |   `2005`  |    `3`    |

        > *Primeira tabela sem a coluna Transp.*

    2. CodTransp e Transp:

        | CodTransp |   Transp   |
        | :-------: | :--------: |
        |    `1`    | `Transp 1` |
        |    `2`    | `Transp 2` |
        |    `3`    | `Tramsp 3` |

        > *Segunda tabela somente com CodTransp e Transp.*

    Agora, apenas o CodTransp será suficiente, na primeira coluna, para já puxar o CodTransp e o Transp.


## Vantagens

As principais vantagens da normalização de dados são: redução da redundância de dados, agrupamento lógico dos dados, assegura a integridade referencial nos dados, melhora a precisão, bem como o desempenho.


## Desvantagens

Já como desvantagens, temos uma maior complexidade do modelo de dados, bem como maior tempo para desenvovolver e maior número de tabelas.


## Fonte
[Blog do Zouza](https://medium.com/blog-do-zouza/modelagem-relacional-uma-visão-geral-44cd8807fc87), [eHow](https://www.ehow.com.br/interferencia-retroativa-proativa-fatos_61464/) e [Acervo Lima](https://acervolima.com/o-que-e-normalizacao-de-dados/).
