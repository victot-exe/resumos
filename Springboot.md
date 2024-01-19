# Springboot
* != do *Spring-Framework (baseado na injeção de dependências)* o **Springboot** foca na configuração automática (foco em produtividade, padrão de estruturação de projetos)

## Antes do Springboot
**Desafios com a configuração**  
* Dependência individual
* Verbosidade
* Incompatibilidade de versões
* Configurações complexas e repetitivas  

## Starters
**Descritores de dependência**
- [ ] Descreve as dependências que serão necessárias para a aplicação no arquivo pom.xml
~~~
<parent>
    <groupId>org.springframework.boot</groupId>
    <artefactId>spring-boot-starter-parent</artefactId>
    <version>2.3.4.RELEASE</version>
    <relativePath> <!-- lookup parent from repository -->
</parent>
<dependencies>
    <dependency>
    </dependency>
</dependencies>
~~~  
  
**Benefícios**
* Coesão -> já avalia desde o início as dependências necessárias. 
* Versões compatíveis -> já tem previamente homologado as qual versão do Springboot suporta qual versão de uma dependência. 
* Otimização do tempo -> 
* Configuração simples -> (não precisa se preocupar com as dependências macro) a própria dependência já tem quais dependências ela precisa. 
* Foco no negócio ->  
**Alguns dos Starters mais utilizados**
- [x] data-jpa -> integra banco de dados (DB) via JPA - Hibernate.
- [x] data-mongodb -> integra DB MongoDB.
- [x] web -> Inclusão do container Tomcat para apps REST.
- [x] web-services: Web-services baseados na arquitetura SOAP.  
- [x] batch -> Implementação de JOBs de processos.  
- [x] test -> testes unitários com JUnit.  
- [x] openfeign -> Cliente HTTP baseado em interfaces.  
- [x] actuator -> Gerenciamento de monitoramento da aplicação.  

## Bean x Component
- [x] Quando usar `@Bean` -> essa anotação é usada em métodos de uma classe de configuração `@Configuration`, este método retorna objetos que o Spring registra no contexto da aplicação como beans gerenciáveis.
-  Métodos com essa anotação criam e configuram o objeto que será gerenciado pelo Spring.
- O objeto é adicionado ao contexto da aplicação e pode ser injetado em outras partes do código. 
- É uma abordagem que permite a personalização sobre como faremos pra injetar a dependência da classe em outras partes do código de uma forma padrão.
~~~
@Configuration
public class AppConfig{
    @Bean
    public MinhaClasse minhaClasse(){
        return new MinhaClasse()
    }
}

//A classe MinhaClasse
public class MinhaClasse{
    private String mensagem;
    
    public MinhaClasse(String mensagem){
        this.mensagem = mensagem;
    }
    
    public String getMensagem(){
        return mensagem;
    }
}

//Injetando a dependência
@Service
public class MeuServico{
    private MinhaClasse minhaClasse;
    
    @AutoWired
    public MeuServico(MinhaClasse minhaClasse){
        this.minhaClasse = minhaClasse;
    }
}
~~~

- [x] Quando usar `@Component` -> marca classes de serviços simples como compents gerenciados pelo spring
- Classes simples que não requerem uma configuração detalhada.
~~~
@Component
public class MinhaClasse{
    private String mensagem = "Hello!";

    public String getMensagem(){
        return mensagem;
    }
}

//Agora podemos injetar diretamente em uma classe
public class MeuServico{
    private MinhaClasse minhaClasse;

    @AutoWired
    public MeuServico(MinhaClasse minhaClasse){
        this.minhaClasse = minhaClasse;
    }
}
~~~

- [x] Beans vsus Components

- [x] Implementar a *IoC* e a *DI (dependence injection)*
