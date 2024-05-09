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
