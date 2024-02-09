# APIs
### O que são?
APIs funcionam como se fosse um carteiro, que pode levar uma mensagem de um programa para o outro, fazendo a comunicação entre cliente e servidor.  

### Criando a API
Com o Cli digite o comando:
~~~powershell
dotnet new webapi --use-controllers
~~~

### EndPoints
Em desenvolvimento de software com .NET, "endpoints" se refere aos pontos de entrada em um aplicativo ou serviço que podem ser acessados por clientes externos para interagir com o sistema.  

Esses endpoints podem ser expostos por meio de diferentes tipos de tecnologias de comunicação, como APIs RESTful, serviços WCF (Windows Communication Foundation), endpoints HTTP, serviços gRPC, entre outros.  

Por exemplo, em uma aplicação web, os endpoints podem incluir URLs que respondem a solicitações HTTP GET, POST, PUT e DELETE para realizar operações específicas, como recuperar dados, enviar dados, atualizar recursos e excluir recursos.  

Em resumo, os endpoints são os pontos de comunicação que permitem que os clientes interajam com o seu aplicativo ou serviço .NET, geralmente através de protocolos de comunicação padronizados, como HTTP ou gRPC.

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

### ConectionString
-> Por onde é feita a conexão com o servidor do banco de dados.  
~~~JSON
"ConnectionStrings": {
    "ConecaoPadrao": "Server=localhost\\sqlexpress; Initial Catalog=Agenda; Integrated Security=True"
  }
~~~

### Migrations
* mapemanto que o EF faz previamente das classes para que ele as transforme em tabelas.
* Cria a pasta 'Migrations' que é onde estão as classes que fazem a conversão da classe para o DB.
~~~powershell
dotnet-ef migrations add NomeDaMigration
~~~

=> Realiza a migration pra gente automaticamente a partir dos objetos que extends `DbSet`  
  * Geralmente ficam na pasta 'Context'
~~~C#
public class AgendaContext : DbContext{
  //Criando o construtor fazendo referência ao construtor da classe pai
  public AgendaContext(DbContextOptions<AgendaContext> options) : base(options){

  }

  public DbSet<Contato> Contatos{ get; set; }
}
~~~

=> atualiza o banco de dados
~~~powershell
dotnet-ef database update
~~~

