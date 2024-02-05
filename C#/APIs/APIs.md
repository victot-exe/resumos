# APIs
### O que são?
APIs funcionam como se fosse um carteiro, que pode levar uma mensagem de um programa para o outro, fazendo a comunicação entre cliente e servidor.  

### Criando a API
Com o Cli digite o comando:
~~~powershell
dotnet new webapi --use-controllers
~~~

### Entity Framework **EF**
É uma ferramenta que faz interações com o banco de dados do c#
* Instalando de maneira global, só é necessaria uma instalação
~~~powershell
dotnet tool install --global dotnet-ef
~~~

* adicionando o pacote do **EF** (Precisa adicionar em cada projeto que for ser utilizado)
~~~powershell
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
~~~

### Entidade
* Entidade é a classe que tambem é uma tabela no banco de dados.