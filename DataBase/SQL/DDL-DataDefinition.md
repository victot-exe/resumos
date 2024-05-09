# Manipulando Dados

# Built-in functions
**Funções nativas**  

`COUNT` -> Retorna o número de registros da tabela que atende a uma determinada condição.
~~~SQL
SELECT COUNT(*) NomeASerExibidoNaColuna FROM Produtos

SELECT COUNT (*) QuantidadeProdutosTamanhoM FROM Produtos WHERE Tamanho = 'M'
~~~

`SUM` -> Retorna a quantidade de uma coluna somada entre si.
~~~
SELECT SUM (Preco) PrecoTotal FROM Produtos

SELECT SUM (Preco) PrecoTotal FROM Produtos WHERE Tamanho = 'M'
~~~

`MAX` x `MIN` -> Retorna o valor máximo ou mínimo de uma coluna.
~~~SQL
SELECT MAX(Preco) ProdutoMaisCaroTamanhoM FROM Produtos WHERE Tamanho = 'M'

SELECT MIN(Preco) ProdutoMaisBaratoTamanhoM FROM Produtos WHERE Tamanho = 'M'
~~~

**Concatenando colunas** -> Para juntar colunas dentro de uma mesma fazemos assim:
~~~SQL
SELECT
    Nome + ' - ' + Cor NomeColunaNova
FROM Produtos
~~~

`UPPER` x `LOWER` -> Altera o estilo de escrita da coluna:
~~~SQL
SELECT
    Nome + ' - ' + Cor NomeProdutoCompleto,
    UPPER(Nome) Nome,
    LOWER(Cor) Cor
FROM Produtos
~~~

* Manipulando colunas
~~~SQL
--Criando a coluna
ALTER TABLE Produtos
ADD DataCadastro DATETIME2
--Adicionando um dado as colunas
UPDATE Produtos SET DataCadastro = GETDATE()
--Deletando a coluna
ALTER TABLE Produtos
DROP COLUMN DataCadastro
~~~

`FORMAT` -> Usado para formatar de uma maneira específica
~~~SQL
SELECT
    Nome + ', Cor: ' + Cor + ' - ' + Genero NomeProdutoCompleto,
    UPPER(Nome) Nome,
    LOWER(Cor) Cor,
    FORMAT(DataCadastro, 'dd/MM/yyyy hh:mm')
FROM Produtos
~~~

`GROUP BY` -> Agrupa elementos de uma coluna que atendem a certa condição
~~~SQL
SELECT
    Tamanho,
    COUNT(*) Quantidade
FROM Produtos
WHERE Tamanho <> ''
GROUP BY Tamanho
ORDER BY Quantidade DESC
~~~

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

`JOIN` -> Junta duas tabelas, ele linka as chaves que fazem referência das tables para juntar corretamente.
~~~SQL
--INNER JOIN
SELECT
    *
FROM
    Clientes C --Definindo um nome mais curto para faciliatar a escrita
INNER JOIN Enderecos E ON C.Id = E.IdCliente
~~~
