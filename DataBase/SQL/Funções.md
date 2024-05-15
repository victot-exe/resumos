# Funções

- São objetos de DB que permitem relizar calculos, transformar dados e retornar resultados;  

## Funções definidas pelo usuário (UDFs)

- Funções criadas pelo deve para criar processamento personalizado;

## Funções do sistema

- Funções nativas e pré-definidas;
- Recebem a entrada de dados -> Realiza ações e transforma -> Saída, o resultado pode ser um valor único ou um conjunto de dados;

### Funções para manipulação de:

| string | Comportamento |
| --- | --- |
| `SUBSTRING` | Retorna parte de uma string (`SUBSTRING (expression, start, lenght)`) |
| `RIGHT/LEFT` | Retorna parte de uma string a partir da direita/esquerda (`LEFT (expression, lenght)`) |
| `UPPER/LOWER` | Deixa a string toda em caixa alta ou baixa |
| `TRIM/RTRIM/LTRIM` | Elimina os espaços em branco nas pontas das strings de todos, apenas a direita ou apenas a esquerda |
| `REPLACE` | Substitui os caracteres em uma string (`REPLACE(string_expression, string_original, novo_valor)`) |
| `STUFF` | Insere uma cadeia de caracteres em outra cadeia de caracteres (`STUFF(original_string, lenght, replace_with_expression)`) |
| `STR` |  |
| `LEN` | Retorna o tamanho de uma string |
| `STRING_SPLIT` | Divide uma string em uma lista (`STRING_SPLIT(string, separador)`) |
| `STRING_AGG` | Concatena uma lista em uma string (`STRING_AGG(expression, separator)`) |
| `CHARINDEX` | A Posição inicial da primeira ocorrência se localizada (`CHARINDEX(expressionToFind, o_que_procurar, [index inicial opcional])`) |
| `PATINDEX` | Permite usar wildcards '%' para pesquisar um padrão (`PATINDEX('%oQueProcurar%', expression)`) |
| `FORMAT` | Muda a formatação com reconhecimento de localidade (`FORMAT(value, format, [culture])`) |
| `CONCAT` | Concatena strings, e pode ser usado apenas com o `+`. |
| **Date** |   |
| `GETDATE()` | Retorna a data atual do servidor |
| `SYSDATETIMEOFFSET()` | Retorna a data atual do servidor com o fuso horário |
| `DAY(SYSDATETIMEOFFSET())` | Retorna o dia da data especificada |
| `MONTH(SYSDATETIMEOFFSET())` | Retorna o mês da data especificada |
| `YEAR(SYSDATETIMEOFFSET())` | Retorna o ano da data especificada |
| `DATEPARTY(yy, SYSDATETIMEOFFSET())` | Retorna a parte da data especificada, desde os ms até as semanas |
| `DATEDIFF(day, 'DataInicial', 'DataFinal')` | retorna a diferença entre duas datas de acordo com a medida de tempo desejada(day, year, minute...) |
| `DATEADD(year, 1, GETDATE())` | Adiciona um tempo na data, o tempo é especificado antes e a quantidade no meio, por fim a data inicial, |
| `DATEFROMPARTS(<year>, <month>, <day>)` | Retorna a data a partir de partes |
| `EOMONTH(DATA, [1 ou -1])` | Retorna o ultimo dia do mes de uma data, para o mes seguinte colocar 1, e o anterior -1 |
| `SWITCHOFFSET(<dataComTimeZone>, <timezone>)` | Altera o fuso horário da data |
| **Matemáticas** |   |
| `ABS()` | Retorna o valor absoluto |
| `POWER(value, potencia)` | retorna a potência indicada |
| `FLOOR()` | Retorna o maior inteiro menor ou igual a expressão |
| `ROUND(valor, precisão)` | Arredonda decimais |
| `RAND` | Valor aleatório / randômico entra 0 e 1 |
| **Agregação** | *Funções matemáticas ou estatisticas em um conjunto de valores, retornando um único valor* |
| `COUNT` | é usado para contar quantas linhas tem no agrupamento |
| `SUM` | Calcula a soma dos valores da coluna |
| `AVG` | CAlcula a média dos valores de um agrupamento |
| `MIN`/`MAX` | Retorna o valor mínimo/máximo da coluna ou expressão. (pode ser usada com numeros, datas e strings) |
| `GROUP BY` | Agrupa os resultados de uma consulta com base em uma ou mais colunas |
| **Classificação** |   |
| `RANK`/`DENSE_RANK()`/`ROW_NUMBER` | Retorna a classificação da linha no conjunto de resultados(classificação = 1 + qtd de classificações acima da linha) `RANK() OVER([partition_by_clausa] ORDER BY order_by_clause)` |