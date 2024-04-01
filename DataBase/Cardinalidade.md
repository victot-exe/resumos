# Cadinalidade
**É a quantidade de ocorrências de uma entidade que pode ser associada a uma ocorrência de outra entidade**  

* `1:n` _1 pra muitos_ -> 1 cliente tem varias encomendas e 1 encomenda é de apenas 1 cliente.
* `n:n` _muitos para muitos_ -> 1 autor escreve varios livros e 1 livro é escrito por varios autores.
* `1:1` _1 pra 1_ -> 1 pessoa possui uma habilitação e 1 habilitação pertence a 1 pessoa.
    - A entidade mais fraca recebe a chave estrangeira da entidade mais forte.
* Cardinalidade mínima -> numero mínimo de ocorrências pode ser 0 dependendo do caso.
