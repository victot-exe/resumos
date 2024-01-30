# Juntar com o do colegio 

* Consulta
* `FILTER` -> como se fosse o WHERE
~~~JSON
FILTER {"cor": "colorido"}
~~~

* `PROJECT` -> Como se fossem as colunas.
~~~JSON
PROJECT {"nome": 1, "Preco": 1, "_id": 0}
~~~
* `SORT` -> COmo se fosse o order by
~~~JSON
SORT{"Preco": 1} --Crescente
SORT{"Preco": -1} --Decrescente
~~~

**Consultas pelo shell**
~~~
db.produtos.find({ Cor: "colorido" }, { Nome: 1, Preco: 1, _id: 0}).sort({Preco: -1})
db.produtos.find({ Cor: "colorido",Preco: {$lte: 50} }, { Nome: 1, Preco: 1, _id: 0}).sort({Preco: -1})
~~~
lte -> less than e -> menor que ou igual  
lt -> less than -> menor que  

**Atualizando pelo shell**
~~~
db.produtos.updateOne(
    {id: 2},
    {$set {Preco: 15.99} }
)
~~~
**Deletando**
~~~
db.produtos.deleteOne({id: 49})
db.produtos.deleteMany({id: 49})

~~~