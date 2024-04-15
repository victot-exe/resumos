# Normalização dos dados
* Conjunto de regras que ajuda a organizar um projeto de banco de dados para:
    * Reduzir a redundância;
    * Aumentar a integridade;
    * Aumentar o desempenho do acesso;

## 1ª Forma Normal
[x] Tem chave primaria definida;  
[x] Cada coluna da tabla contem apenas valores atômico( Indivisíveis);  
[x] Não tem valores repetidos em uma mesma coluna;  

## 2ª Forma Normal
[x] Deve estar na 1ª Forma Normal;  
[x] Não existe dependência parcial;  
    * Cada atributo não-chave deve ser totalmente dependente de todas as partes da chave primária.

## 3ª Forma Normal
[x] Deve estar na 2ª Forma Normal;  
[x] Não exista dependências transitivas;  
    * Nenhuma coluna não-chave dependeter de outra coluna não-chave;
