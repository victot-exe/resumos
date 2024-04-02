# TypeScript
* Um SuperSet do JavaScript que nos permite tipar os valores
~~~typescript
var texto: string = ""
var numero: number = 123
var verdadeiro: boolean = false
var date: Date = new Date()
var dinamico: any

//arrays
var numeros: number[] = []
var textos: string[] = []
var dinamicos: any[] = []

//Tipo variado
let minhaVariavel: number | string | boolean
minhaVariavel = 12212
minhaVariavel = ""
minhaVariavel = false

//Tipo proprio
type Pessoa = {
    nome: string
    descricao: string
}
var pessoa: Pessoa = {nome:"Victor", descricao:"Dev"}

console.log(pessoa)

//funcoes
function mostrarTexto():string{
    return "texto"
}

function mostrarNumero(): number{
    return 123
}

function mostrarTexto1(texto:string):string{
    return `Texto => ${texto}`
}

function metodo():void{
    console.log("Fez alguma coisa")
}

function ex():any{
    return 123
}

function exArray():any[]{
    return [1, 2, 3, "str"]
}
~~~
* Classes em Ts
~~~typescript
export interface IAnimal {//o export é para que a interface seja visível em outros arquivos
    nome: string
    andar(): void
    correr(): void
    emitirSom(): string
}
~~~
~~~typescript
import { IAnimal } from "./IAnimal"

export class Gato implements IAnimal{
    nome: string;

    constructor(nome: string){
        this.nome = nome
    }
    
    andar(): void {
        console.log(`O gato ${this.nome} está andando.`)
    }
    correr(): void {
        console.log(`O gato ${this.nome} está correndo.`)
    }
    emitirSom(): string {
        return "MIAAAAU"
    }
}
~~~
**Utilizando a classe**
~~~typescript
import { Gato } from "./Objetos/Gato";

var gato = new Gato("frajola")

gato.correr()
var miando = gato.emitirSom()

console.log(`Som do gato => ${miando}`)
~~~
