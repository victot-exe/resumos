# SQL
**Structutrd Query Language** -> linguagem de *DB* usada para consulta e manipulação de dados.  
## Database *DB*
- [x] É uma coleção de dados estruturados, agrupados de forma concisa
- [x] É composto de: 
- Tabelas -> 
- Procedures -> 
- Views -> 
- Etc...
*Semelhante a uma tabela do Excel* -> divido em tabelas, que são divididas em linhas *(rows)* e colunas *(columns)*.  

## SQL commands

### DDL *- Data Definition Language*
- [x] CREATE -> Cria uma tabela
~~~
CREATE TABLE Produtos(
    Id int IDENTITY(1,1) PRIMARY KEY NOT NULL,
    Nome varchar(255) NOT NULL,
    Cor varchar(50) NULL,
    Preco decimal(13, 2) NOT NULL,
    Tamanho varchar(5) NULL,
    Genero char(1) NULL
)
~~~
`IDENTITY` -> Deixa o campo automático, o proprio banco incrementa esse valor
`PRIMARY KEY` -> define como chave primária, não deixando aquele valor se repetir

- [x] DROP ->
- [x] ALTER ->
- [x] TRUNCATE ->

### DCL *- Data Control Language*
- [x] GRANT ->
- [x]  REVOKE ->

### DML *-Data Manipulation Language*
- [x] INSERT -> Insere dados na tabela
~~~
INSERT INTO Clientes (Nome, Sobrenome, Email, AceitaComunicados, DataCadastro)
VALUES ('Victor', 'Faria', 'email@email.com, 0, GETDATE())
~~~
*Entendendo o ID, é um identificador único que não pode ser repetido nas tabelas.*

- [x] UPDATE -> Atualiza o dado de alguma coluna/linha
~~~
UPDATE Clientes
SET Email = 'emailatualizado@email.com',
    AceitaComunicados = 0
WHERE Id = 1002
~~~
*Atualizar sempre pelo Id, para evitar que muda o que não deve ser modificado.*

- [x] DELETE -> Deleta o dado selecionado
~~~
DELETE Clientes
WHERE Id = 1001
~~~
*Tomar os mesmos cuidados do `UPDATE` para não acabar apagando algo que não devia.

### TCL *-Transition Control Language*
- [x] COMMIT ->
- [x] ROLLBACK ->
- [x] SAVEPOINT ->

### DQL*-Data Query Language*
- [x] SELECT -> Comando usado para consultar os dados do *DB*  
    `SELECT * FROM Clientes` => Exemplo de consulta básica que mostra todos os dados de uma tabela por ordem de inserção.  
    `WHERE` -> Usado para filtrar os dados da seleção
    ~~~
    SELECT * FROM Clientes
    WHERE Nome = 'Adam' AND Sobrenome = 'Reynolds'
    ~~~
    -[ ] Seleciona todos os registros que atende aos parametros colocados após o `WHERE`, Usamos o AND, OR
    ~~~
    SELECT * FROM Clientes
    WHERE Nome LIKE 'G%'
    ~~~
    - [ ] O `LIKE` diz que o nome precisa conter.
    - [] O `%` é usado para dizer se a parte especificada vem no começo `G%`, no meio `%G%` ou no final `%G`

    `ORDER BY` -> Usado após o `SELECT` ordenar os dados por alguma coluna.
    ~~~
    SELECT * FROM Clientes
    ORDER BY Nome, Sobrenome
    -- Usar o DESC para forma decressente, pode se usar mais de uma coluna para ordenação, colocando na sequencia separando por virgula.
    ~~~

    **Selecionando colunas**  
    * O `*` Seleciona tudo, para selecionar apenas algumas basta especificar  
    `SELECT Email FROM Clientes` => Tras apenas a coluna Email da tabela clientes.  

### Tipos de dados
- Tipos de dados que serão definidos no momento da criação da tabela:
    **String**
    - `char(n)` -> Quando vai ter sempre o mesmo tamanho de carcteres Sigla de estado, etc...
    - `varchar(n)` -> Quando não tem certeza do numero de caracteres.
    **Numericos**
    - `bit` -> 0, 1, null (usa-se para boolean).
    - `int` -> 
    - `decimal` -> monetários
    **Date and Time**
    - `datetime2` ->
    - `date` -> apenas a data
    - `time` -> apenas a hora

### PK & FK
* PrimaryKey -> Chave única que identifica cada registro na tabela.
* ForeignKey -> Chave que identifica um registro existente em outra tabela.
~~~SQL
CREATE TABLE Enderecos(
    Id int PRIMARY KEY IDENTITY(1, 1) NOT NULL,
    IdCliente int NULL,
    Rua varchar(255) NULL,
    Bairro varchar(255) NULL,
    Cidade varchar(255) NULL,
    Estado char(2) NULL,
    --Definindo uma FOREGEIN KEY
    CONSTRAINT FK_Enderecos_Clientes FOREIGN KEY(IdCliente)
    REFERENCES Clientes(Id)
)
~~~
