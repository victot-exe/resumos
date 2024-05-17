# DML - Data Manipularion Language

- `SELECT` => Recupera linhas do DB e permite a seleção das collumns que serão exibidas;(Tipos ntext, text e image não podem ser utilizados)
- `INSERT` => Insere dados a uma tabela;
- `UPDATE` => Atualiza os dadados de uma tabela;
- `DELETE` => Exclui os dados de uma tabela;
- `MERGE` => Realiza as operações de inserção, atualização ou exclusão em uma table de destino com base em uma consulta;  
- Sintaxe da consulta:  
`COMANDO_DML` coluna_da_table `as` titulo-mostrado-no-resultado,  
                outra_coluna `as` titulo-da-outra  
`FROM` tabela_de_origem Nome-a-ser-exibido

- `DISTINCT` => É usado em consultas SQL para remover registros duplicados do resultado da consulta;
- `ORDER BY` => Usado para ordenar os resultados de acordo com uma ou mais collumns, usando o `ASC` para ascendente e `DESC` para decrescente;

~~~SQL
SELECT tn.release_year, tn.title
FROM dbo.titles_netflix tn
ORDER BY tn.release_year DESC, tn.title ASC
~~~

- `WHERE` => É usado para filtrar os resultados de uma consulta

~~~SQL
SELECT tn.*
FROM dbo.titles_netflix tn
WHERE tn.Title = 'Kung Fu Panda 3'
~~~

- Operadores => São usados para colocar condições no `WHERE`

| Operador | Significado |
| --- | --- |
| `=` | Igual a |
| `>` | Maior que |
| `<` | Menor que |
| `>=` | Maior ou igual |
| `<=` | Menor ou igual |
| `!=` ou `<>` | Diferente de |

- Operadores lógicos => usados para colocar mais de uma condição nas causas do `WHERE`;

| Operador | Significado |
| --- | --- |
| `AND` | True se as duas condições forem true |
| `OR` | True se qualquer das condições for true |
| `NOT` | Inverte o valor de outro operador bool |
| `EXISTS` | True se a subconsulta tiver qualquer linha |
| `IN` | True se o valor for igual a um de uma lista de expressões |
| `LIKE` | True se o valor corresponder a um padrão |
| `BETWEEN` | True se o valor estiver dentro de um intervalor |

## Subconsultas

- São consultas aninhadas dentro de outras consultas;

~~~SQL
SELECT p.FirstName, p.LastName
FROM Person.Person AS p
WHERE p.BusinessEntityID IN
                (
                    SELECT BusinessEntityID
                    FROM Sales.SalesPerson
                    WHERE SalesQuota > 250000
                )
~~~

## JOIN

- `JOIN` => Junção, é o operador usado para unir dados entre duas tabelas considerando o relaionamento entre as colunas. (Geralmente essas colunas são chaves primárias ou estrangeiras);

~~~SQL
SELECT tn.id, tn.title, cn.name
FROM dbo.titles_netflix tn
INNER JOIN dbo.credits_netflix cn
            ON tn.id = cn.title_id
~~~

| Tipo JOIN | Comportamento |
| --- | --- |
| `INNER JOIN` | Relaciona os registros da table da esquerda ( `FROM` ) com os registros da table da direita (Intersecção => Retorna apenas os registros que tem correspondência nas duas tables)  |
| `LEFT (OUTER) JOIN / RIGHT JOIN` | Todos os registros da table da esquerda relacionadas com os registros da direita, inclusive nulls |
| `FULL (OUTER) JOIN` | Todos os registros de ambas as tables incluindo os valores NULL (União) |
| `UNION` | Concatena o resultado de duas ou mais consultas em um unico conjunto de resultados |
| `UNION ALL` | Faz o que o `UNION` faz só que incluindo os registros duplicados |
| `EXCEPT` | Retorna as linhas da primeira consulta exceto as linhas que existam na segunda consulta|
| `INTERSECT` | Retorna as linhas em comum entre as duas consultas (Intersecção) |

## Manipulando dados

 - `INSERT` -> Usado para inserir novos registros em uma table;
    1. A cada novo registro, as restrições de obrigatoriedade(NOT NULL), referências(FK), e chaves unicas serão verificadas;
    2. Colunas com autoincremento(IDENTITY) devem ser omitidas para a inserção, já que o valor será unico e dado pelo sistema;
    3. Colunas DEFAULT e não obrigatorias podem ser omitidas;

- Sintaxe
~~~SQL
INSERT INTO [schema].[table] ([(lista colunas, ...n)])
VALUES ([lista de valores, ...n])
--ou
INSERT INTO [schema].[table] ([(lista colunas, ...n)])
SELECT [(lista colunas, n)]
FROM [schema].[table]
--ou
SELECT *
INTO [schema].[nova_table]
FROM [schema].[table]
~~~

- `UPDATE` -> Altera dados de uma table;

- Sintaxe
~~~SQL
UPDATE [table]
SET NomeColuna1 = Valor,
    NomeColuna2 = Valor
[WHERE (condicoes)]
~~~
