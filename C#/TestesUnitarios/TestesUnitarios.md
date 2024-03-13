# Testes unitários
Testa a menor parte do programa, para prevenir erros da aplicação.  
Encontrar, resolver e validar erros.  
Os testes podem ter o resultado tanto positivo quanto negativo.  

## Vantagens
* Ajuda a garantir a qualidade do código;
* Diminui bugs;
* Garante que a alteração não tenha impactos no sistema;
* Maior confiança de que suas classes e métodos funcionam;
* Prevenir erros futuros.

## Frameworks utilizados
* MSTest (Microsoft Test);
* NUnit;
* xUtit; `mais utilizado`  
__São muitos parecidos mas um muda um pouco de um para o outro__

## Convenções dos testes
* Para testar colocar dentro de uma classe com o nome da classe testada + Test;
* O nome do método deve ser descritivo sobre o que ele vai testar;
* 

### Conceitos
1. Arrange -> Monta o cenário de teste;
2. Act -> Após o cenário chama o mesmo para o teste;
3. Assert -> Validar se o resultado foi o resultado esperado.
~~~C#
public class CalculadoraTests
{
    private CalculadoraImplementacao _calc;

    public CalculadoraTests()
    {
        _calc = new CalculadoraImplementacao();
    }

    [Fact]//Faz considerar o método como um método de teste
    public void DeveSomar5Com10ERetornar15()
    {
        //Arrange
        int a = 5, b = 10;
        //Act
        int resultado = _calc.somar(a, b);
        //Assert
        Assert.Equal(15, resultado);
    }
}
~~~  
__Para executar o teste `dotnet test`

#### Verificando mais de uma possibilidade por método
* `Theory`-> conjunto de dados que é passado para o método e ele valida a cada execução.
~~~C#
[Theory]
    [InlineData(2)]
    [InlineData(4)]
    [InlineData(6)]
    [InlineData(8)]
    [InlineData(10)]
    public void VerificaSeOsNumerosSaoParesERetornarVerdadeiro(int num)
    {
        //Arrange
        //Act --> ele vai verificar cada um dos InLineData no teste sem precisar escrever varios métodos
        bool resultado = _calc.isPar(num);
        //Assert
        Assert.True(resultado);
    }
~~~
* Podemos colocar listas ao inves de passar numero por numero, tendo o mesmo resultado.
~~~C#
[Theory]
    [InlineData(new int[] { 2, 4})]
    [InlineData(new int[] { 6, 8, 10})]
    public void VerificaSeOsNumerosSaoParesERetornarVerdadeiro(int[] nums)
    {
        //Act / Assert
        Assert.All(nums, num => Assert.True(_calc.isPar(num)));
    }
~~~
