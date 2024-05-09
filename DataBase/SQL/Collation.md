# Collation
- Termo usado para definir o conjunto de regras que o SQL Server irá utilizar para ordenação e comparação entre textos:
`SQL_Latin1_General_CP1_CI_AS` -> Mais utilizado para idiomas latinos.  

| Elemento | Signigicado |
| :---: | :--|
| `SQL` | Collation exclusiva do SQL Server |
| `Latin1_General` | Suporta alfabeto latino |
| `CP1` | Code page 1 - tabela de caracteres Windows-1251 |
| `CI` | Case Insensitive - não diferencia upper de lower case (A == a) |
| `AS` | Accent Sensitive - diferencia caracteres com e sem acento |

`SELECT DATABASEPROPERTYEX('DbName', 'Collation') AS DBCollation` -> Para verificar a colattion do DB. 
`EXEC sp_help 'nome_da_table'` -> Verifica a collation de uma collumn.  
 