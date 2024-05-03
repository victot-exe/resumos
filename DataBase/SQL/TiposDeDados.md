# Tipos de dados
- **No que interfere?**
    - Precisão -> dados precisos e completos, ex: ter casas decimais o suficiente;
    - Eficiência -> otimizar a performance das consultas e operações;
    - Legibilidade dos dados -> Melhora a compreensão das informações;

## Categorias
| Tipo | Descrição | Capacidade |
| ---: | :-------: | :--------- |
|      | **String** |           |
| char(n)| Cadeia de caracteres fixa.n = quantidade de caracteres | 8000 caracteres |
| varchar(n) | Cadeia de caracteres variável.n = quantidade de caracteres | 8000 caracteres |
| text | Cadeia de caracteres variável (para grandes quantidades de texto 2GB) | 1073741824 caracteres |
| nchar(n) | char(n) só que em unicode | 4000 caracteres |
| nvarchar(n) | nchar(n) só quem em unicode | 4000 caracteres |
| nvarchar(max) | Cadeia de caracteres variável com tamanho máximo de 2GB | 536.870.912 caracteres |
| ntext | text em unicode | @2GB |
| binary(n) | Dados binários com tamanho fixo | 8000 bytes |
| varbinary(n) | Dados binários com tamanho variável | 8000 bytes |
| varbinary(max) | Dados binários com tamanho variável | 2GB |
| image | Dados binários com tamanho variável | 2GB |
|       | **Numéricos** |       |
| bit | 0, 1 ou NULL (usado para true-1 or false-0) | 1 byte |
| tinyint | 0 a 255 | 1 byte |
| smallint | de -32768 a 32767 | 2 bytes |
| int | de -2147483648 a 2147483647 | 4 bytes |
| bigint | -9223372036854775808 a 9223372036854775807 | 8 bytes |
|        | **Números de precisão fixa e escala** |   |
| decimal (p, s) | p = num.precisão(padrão 18), s = escala(padrão 0) | 5-17 bytes |
| smallmoney | -214748,3648 a 214748,3647(máximo 4 casas decimais) | 4 bytes |
| money | -922337203685477,5808 a 922337203685477,5807 | 8 bytes |
| float(n) | ponto flutuante de -1,79E+308 a 1,79E+308 | 4 ou 8 bytes |
| real | equivalente a um float(24) | 4 bytes |
|        | **Data e hora** |   |
| datetime | de 01/01/1753 a 31/12/9999 e h 00:00:00 a 23:59:59.997 | 8 bytes |
| datetime2 | de 01/01/0001 a 31/12/9999 e h 00:00:00 a 23:59:59.9999999 | 6-8 bytes |
| smalldatetime | de 01/01/1900 a 06/06/9999 h 00:00:00 a 23:59:00 (sem segundos) | 4 bytes |
| date | apenas data 01/01/0001 a 31/12/9999 | 3 bytes |
| time | Apenas hora de 00:00:00.0000000 a 23:59:59.9999999 | 3-5 bytes |
| datetimeoffset | Data e hora de 01/01/0001 até 31/12/9999 e fuso horário de -14:00 a +14:00 | 8-10 bytes |

## Conversão de tipos de dados
### Implicita
- O SQL faz a conversão de maneira automática e de forma implicita (sem ser declarada no código):
~~~SQL
DECLARE @Numero INT
SET @Numero = '10'
~~~
### Explícita
- Recebe a instrução para conversão
~~~SQL
CONVERT (DATE, '2022-06-02')
CAST ('10' AS INT)
~~~
*Algumas conversões não são possíveis e algumas são convertidas mas com perda de dados (float para int por ex)*