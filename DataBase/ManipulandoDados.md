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

