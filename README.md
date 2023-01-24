# SQL Server
Criando banco de dados SQL Server.

Inicialmente vamos tentar apresentar os comandos DDL (Data Definition Language), DML (Data Manipulation Language) e o DCL (Data Control Language), no qual são os comandos que criam, gerenciam e administram os Bancos de Dados:

## **DDL (Data Definition Language)**

Os comandos **DDL** **criam os componentes do banco de dados**, ou seja, as entidades, além de fazer a manutenção de sua estrutura. Sendo assim, a produção de tabelas e índices, bem como sua manutenção, são feitas através destes comandos, o famoso CRUD. Entre eles, podemos citar os seguintes:

- `create` - cria tabelas, índices e outras estruturas;
- `alter` - altera as propriedades das entidades;
- `truncate` - apaga definitivamente os dados de uma tabela;
- `drop` - apaga não apenas os dados, mas própria tabela do banco de dados;
- `rename` muda o nome de alguns componentes do banco.

## **DML (Data Manipulation Language)**

São usados para **gerenciar os dados do banco**, ou seja, informações que estão, por exemplo, dentro das tabelas. Alguns exemplos de comandos **DML** são:

- `insert` - inclui dados em uma tabela;
- `update` - altera dados de uma tabela;
- `delete` - apaga dados da tabela;
- `lock` - gerencia concorrência da atualização de dados de uma tabela.

## **DCL (Data Control Language)**

É o conjunto de comandos que permite administrar o banco de dados. Essa administração não trata da estrutura do banco, mas sim de **componentes como segurança, usuário e forma de armazenação dos dados**. Entre estes comandos, podemos citar os seguintes:

- `commit` - salva o estado do banco de dados de forma definitiva;
- `rollback` - retorna ao estado salvo previamente;
- `savepoint` - salva o estado do banco de forma temporária.

Ato continuo, também, se faz necessário apresentar as 'ENTIDADES'.

## ***Definição de Entidades***

Dentro de um banco, existem várias entidades. A primeira e mais importante é a tabela (tables). Um banco de dados SQL Server pode ter uma ou mais tabelas, dentro das quais os dados ficam armazenados. Podemos afirmar que uma tabela se assemelha à uma planilha de Excel, já que é composta por colunas e linhas. Mas, apesar da semelhança, existem diferenças significativas. Vamos nos ater a elas.

Na tabela, o número de linhas é limitado somente pelo espaço em disco disponível para armazenagem do banco. Sendo assim, podem existir tabelas com milhões ou bilhões de linhas. Já no que diz respeito ao número de colunas, o valor é limitado, sendo definido no momento de estruturação da tabela. É possível incluir e excluir colunas apenas em casos específicos que envolvem as regras, das quais falaremos adiante. Vale ressaltar que as linhas são chamadas de **registros**, e as colunas, de **campos.**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8467d4a1-f7eb-4f8c-81c2-9c4e7d85364d/Untitled.png)

Quando definimos o campo, a propriedade mais importante é o seu nome, que deve respeitar algumas regras. Esse nome deve ser único, portanto, não podemos ter mais de um campo com a mesma nomenclatura.

## ***Campos possuem definições rígidas***

Outra importante característica é a definição dos dados dentro de um campo. Os dados de determinado campo devem ser do mesmo tipo, ou seja, cada campo/coluna possui um tipo único. Assim, ao definir uma coluna como do tipo texto, todas as suas linhas devem conter dados correspondentes ao tipo definido. O tamanho do campo também é um atributo importante, pois, para alguns tipos de campo, o tamanho é previamente especificado. Se definimos um campo como do tipo texto, com 20 caracteres, por exemplo, não poderemos escrever um dado que ultrapasse esse tamanho.

A coluna pode, ainda, aceitar ou não valores vazios. Neste aspecto, precisamos estar atentos à diferença entre valor vazio e valor em branco, sendo o vazio a ausência de valor. Se definirmos que um campo não aceita valor vazio e criarmos uma linha nova, ela obrigatoriamente precisa ter algum valor. Pode-se, ainda, existir valores padrões. Assim, ao criarmos uma linha e não preenchermos o valor a ser gravado nele, o SQL Server gravará um valor *default* (padrão).

Vale ressaltar que todas essas características são definidas no momento da criação da tabela.

## ***Chaves primárias (primary key)***

Em uma tabela, podemos classificar um ou mais campos como sendo campos de **chaves primárias**. Quando temos uma coluna assim definida, os valores não podem se repetir dentro das linhas desse campo.

No caso de chaves primárias compostas, em que temos mais de um campo como chave primária da tabela, o conjunto de valores entre esses campos não pode se repetir em outras linhas.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/26841b51-318f-425e-8f14-204126760830/Untitled.png)

Vamos à um exemplo para melhor entender o conceito de chave primária.

Supondo que temos uma tabela com cadastro de cliente, sabemos que CPF é um número único para cada indivíduo. Se definimos que o campo CPF é uma chave primária, não podemos ter clientes com o mesmo CPF. Outros exemplos de seu uso, são siglas de estados e códigos de produtos.

A chave primária é usada para que busquemos determinada linha, mas seu uso não é obrigatório, portanto, uma tabela pode existir sem ter chaves primárias.

## *****Chaves estrangeiras (foreign key) e cardinalidade*****

Esta chave estabelece uma relação entre 2 campos de tabelas diferentes, que devem ter as mesmas propriedades. Ela liga o campo normal de uma tabela com um campo que é chave primária de outra, e a relação de **cardinalidade**  entre esses campos deve ser de 1 para N **(1:N)**.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c7c877cf-af2f-40c6-9844-eb1b787ec983/Untitled.png)

Vamos supor que temos uma tabela de estado e outra de clientes. Na tabela de clientes, temos um campo que representa o estado onde cada um mora. Nessa tabela, o identificador desse cliente é a chave primária, ou seja, o código do cliente que não se repete. Mas o campo de estado pode se repetir, já que é possível ter mais de um cliente no mesmo estado.

Este campo de estado, na tabela de clientes, tem uma chave estrangeira com o campo estado da tabela de estados. Ou seja, na tabela de estados, esse campo é a chave primária, já que as siglas dos estados são únicas e não podem se repetir.

Ao criar a chave estrangeira, é criado um vínculo entre esses dois campos, e não podemos, portanto, ter um cliente com um estado que não esteja presente na tabela de estados. Caso isso aconteça, um erro será gerado.


Desta forma apresento e defino o CRUD, bem como as definições necessárias como realizar a criação de tabela em um Banco de Dados, conforme modelo neste Diretorio.

Curso de Fundamentos do SQL Server do Balta.io e Alura

Anotações no Notion: https://www.notion.so/Fundamentos-do-SQL-Server-85841fb1ddfe42c09291abce2b899e37

Certificado de conclusão de curso: https://balta.io/certificados/a96c5a63-add0-417f-9417-d2d5e96a7d95
