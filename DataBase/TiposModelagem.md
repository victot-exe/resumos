# Modelagem relacional
* Ajuda a identificar as entidades e atribustos dos dados;
* Favorece a padronização dos nomes de tableas e atributos;
* identifica relacionamentos e aspectos comins entre os dados;
* Implementa regras de negócio e restrições para evitar inconsistência;
    * Responsabilidade que deve ser dividida entre a camada da aplicação e o DB;
* Cada linha com uma identificação única;
* Organizar os dados e reduzir a redundância (normalização dos dados);
* Melhorar o desempenho das consultas e operações;
* Implementar o **ACID** junto com o **SGBD**;

## Entidade e atributos
* Entidade->Atributo->Dominio dos dados
* Entidadade
* Atributos: Descreve as caracteristicas da entidade;
* Domínio dos dados: Define o tipo de dados e as restrições que serão aplicadas;

## Restrição em modelo relacional
* Restrições de domínio: Tipo dos dados -> int, bool, char, date;
* Restrições sobre valores vazios: Se null é permitido ou não.
* Restrições de chave primária: Garante que o atributo que identifica o registro seja único, evitando duplicidade;
* Restriç~es de chave estrangeira: Estabelece um relacionamento entre duas tables, garantindo a integridade referêncial;

## Chave
* Um ou mais atributos que identificam uma linha ou conjunto de linhas;
### Chave primária
* Conjunto de um ou mais atributos que identificam um registro;
* Garante a integridade dos dados;
* Usado para criar relacionamento entre tabelas;
#### Chave candidata
* Atributos ou uma combinação de atriustos que podem ser usados como chave primária;
* Pode ser um atributo ou combinação de atributos;
* O valor ou a combinação deve ser único;
* Não pode ser null;
* Deve ser irredutível. (não pode ser dividido ou decompostoo);
* Evitar atributos que possam ser alterados;
* Quando não existe chave candidata-> Criar atributo com auto incremento (IDENTITY), gera um valor numérico sequencial que a cada novo registo é incrementado (+1) gerando um código único.
* Riscos e cuidados;
### Chave estrangeira
* Atributo em uma table que faz referência a uma chave primária em outra table;

## Cardinalidade

* Quantidade de ocorrências de uma entidade que pode ser associada a outra;
* Cardinalidade mínima pode ser 0 ou 1;
* 1:n -> 1 para muitos = 1 cliente tem muitas encomentas, mas uma encomenda só tem 1 cliente;
* n:n -> Muitos para muitos = 1 autor escreve varios livros e 1 livro é escrito por varios autores;
    * Gera uma nova tabela com relação 1:n para cada table inicial;
* 1:1 -> 1 para 1 = 1 pessoa possui uma cnh e 1 cnh pertence a 1 pessoa;
    * A entidade mais fraca recebe a chave estrangeira da table mais forte;
    * Existem casos onde é melhor a table mais forte absorver as informações da table mais fraca;
    * As tables podem receber as chaves estrangeiras uma da outra;
