# Variáveis
- As variáveis são usadas par armazenar dados temporariamente na memória durante a execução de uma consulta ou procedimento armazenado;
    - Declarando -> `DECLARE @Var1 INT`;
    - Declarando com o valor -> `DECLARE @Var2 VARCHAR(50) = 'Valor'`;
    - Atribuindo o valor -> `SET @Var1 = 10` || `SELECT @Var1 = 20`;
    - Visualizando o valor -> `SELECT @Var1` || `print @Var1`;
- A variável só existe dentro de um bloco de execução;
- Podem ser usadas em operações;

## Variável do tipo table
~~~SQL
DECLARE @TempFruta AS TABLE (Id INT IDENTITY (1, 1), Name VARCHAR(100))

INSERT INTO @TempFruta (Name)
VALUES ('Maçã'), ('Pera'), ('Abacate'), ('Banana'), ('Morango')

SELECT *
FROM @TempFruta t
GO
~~~
