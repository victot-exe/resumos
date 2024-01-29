# Constraints
**Regras definidas para inserção de dados**
* `NOT NULL` -> O valor não pode ser do tipo null.
* `UNIQUE` -> O valor deve ser único em toda a tabela.
~~~SQL
--Definindo um valor como unico, garantindo que não tenha duplicação de produtos.
ALTER TABLE Produtos
ADD UNIQUE(Nome)
~~~

* `CHECK` -> Validação do valor (Ex.: O valor sempre deve ser maior do que zero).
~~~SQL
--Adicionando um nome para a constraint, e definindo a regra para inserção na coluna gênero
ALTER TABLE Produtos
ADD CONSTRAINT CHK_ColunaGEnero CHECK(Genero = 'U' OR Genero = 'M' OR Genero = 'F')
~~~

* `DEFAULT` -> Valor padrão de inserção (Quando não é passado um valor ele já tem um padrão).
~~~SQL
--Deixando o valor da data padrão como o GETDATE() sem precisar escreve-lo toda a vez, caso seja passado outro valor ele é definido no lugar do default no caso atual, não atera os outros
ALTER TABLE Produtos
ADD DEFAULT GETDATE() FOR DataCadastro
~~~

* `PRIMARY KEY` -> Combinação de NOT NULL e UNIQUE.
* `FOREIGN KEY` -> Garante que o registro exista em outra tabela.

### Removendo uma `constraint`
* Depois de pegar o nome correto da `CONSTRAINT` que precisa ser removida.
~~~SQL
ALTER TABLE Produtos
DROP CONSTRAINT NomeDaConstraint
~~~

## Stored Procedures
**Códigos SQL que vc pode salvar diretmante no banco de dados, para ter aproveitamento de código.**
~~~SQL
--Antes teria que chamar essa parte toda a vez que fosse adicionar
INSERT INTO Produros (Nome, Cor, Preco, Tamanho, Genero)
VALUES (@Nome varchar(255), @Cor varchar(50), @Preco decimal, @Tamanho varchar(5), @Genero char(1))
--Para criar uma procedure
CREATE PROCEDURE InserirNovoProduto
@Nome varchar(255),
@Cor varchar(50),
@Preco decimal,
@Tamanho varchar(5),
@Genero char(1)
AS
INSERT INTO Produros (Nome, Cor, Preco, Tamanho, Genero)
VALUES (@Nome, @Cor, @Preco, @Tamanho, @Genero)
--Chamando a stored procedure, pode ser usado EXEC ou EXECUTE
EXEC InserirNovoProduto
'Novo Produto',
'Colorido',
50,
'G',
'U'
~~~
**Também podemos criar procedures de consultas**
~~~SQL
CREATE PROCEDURE ObterProdutosPorTamanho
@TamanhoProduto varchar(5)
AS
SELECT * FROM Produtos WHERE Tamanho = @TamanhoProduto
--EXECUTANDO
EXEC ObetrProdutosPorTamanho 'G'
~~~

## FUNCTIONS
**Codigos SQL que vc pode salvar diretamente no banco de dados, a principal diferença entre ela e a procedure é que a function sempre precisa ter um retorno**
~~~SQL
CREATE FUNCTION CalculadorDesconto(@Preco Decimal(13, 2), @Porcentagem int)
RETURNS decimal(13, 2)
BEGIN
    RETURN @Preco - Preco / 100 * @Porcentagem
END
--Chamando
SELECT
    Nome,
    Preco,
    dbo.CalcularDesconto(Preco, 10) PrecoComDesconto
FROM Produtos WHERE Tamanho 'M'