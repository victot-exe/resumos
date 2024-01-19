# Spring framework
* Framework open source para Java.
- [x] Baseado em inversão de controle **IoC** e injeção de dependência.
- IoC => Redirecionamento do fluxo de execução de um código, retira parcialmente o controle sobre ele e delega a um container. (Minimiza o acoplamento de código).
- Injeção de dependências => padrão de desenvolvimento que tem por finalidade manter o baixo nível de acoplamento entre os módulos do sistemas.
- [x]  Estrutura modular
- Reduz a complexidade das aplicações
#### Módulos do Spring
- [x] **Spring-Framework Runtime**  
- [x] Data Acess / Integration
- JDBC
- ORM
- OXM
- JMS
- Transacrions
- [x] Web
- Web
- Servlet
- Portlet
- Struts
**AOP**  
**Aspects**  
**Instrumentation**  
- [x] **Core Container**  
- Beans => Objeto que é instanciado, montado e gerenciado por um container através do princípio da IoC.
- Core
- Context
- Expression Language
- [x] **Test**
# ------------------------+
#### Scopes (esfera de uma aplicação)
- [x]  Singleton => um único objeto compartilhado pela aplicação quando solicitado, definido pelo IoC.
- [x] Prototype => Cria uma nova instância a cada requisição de um objeto pelo container
- [ ] **HTTP** 
- Request => um bean criado para cada requisição, quando a requisição é finalizada o Bean é destruído. 
- Session => Um Bean criado para cada sessão de usuário (Carrinho de compras de usuário)
- Global => cria um Bean para cada ciclo de vida do contexto de aplicação.

#### Autowired
**Uma anotação que indica onde deve ocorrer uma injeção automática de dependência.**  
* byName -> busca um método set que corresponde ao nome do Bean.
* byType -> é considerado o tipo da classe para inclusão do Bean.
* byConstructor -> usa o construtor para incluir a dependência. 

