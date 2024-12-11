	O OCP afirma que as classes devem estar "abertas para extensão, mas fechadas para modificação".

## Benefícios:
	Facilidade de Extensão: Novas funcionalidades podem ser adicionada sem alterar o código existente;
	Redução de Bugs: Minimiza o risco de introduzir erros em funcionalidades já implementadas.
	Facilidade de Manutenção: Código já existente não é alterado, evitando a introdução de novos bugs.
	Extensibilidade: Novos comportamentos são adicionados por meio de novas classes.

**Dica Final:**
	Pense em como tornar o código extensível. A adição de novas funcionalidades não deve significar modificar o código existente.

**Exemplo de Má Prática:**

	Modificar uma classe diretamente para adicionar um novo comportamento.

## OCP - Mau Exemplo
	Para adicionar um novo tipo de produto, como "Alimentos", precisaríamos modificar a classe CalculadoraDeDesconto, violando OCP.
```C#
public class CalculadoraDeDesconto
{
	public double CalcularDesconto(string tipoProduto, double valor)
	{
		if(tipoProduto == "Eletronico")
			return 0.1 * valor;
		else if(tipoProduto == "Roupas")
			return 0.2 * valor;
		else
			return 0;
	}
}
```

## OCP - Bom Exemplo
	Use polimorfismo para estender o comportamento sem modficar a classe base;
	Solução: Agora, novos tipos de desconto podem ser adicionados criando novas classes, sem modificar a classe CalculadoraDeDesconto original.
```C#
public abstract class Desconto
{
	public abstract double Calcular(double valor);
}

public class DescontoEletronicos : Desconto
{
	public override double Calcular(double valor) => 0.1 * valor;
}

public class DescontoRoupas : Desconto
{
	public override double Calcular(double valor) => 0.2 * valor;
}

public class DescontoAlimentos : Desconto
{
	public override double Calcular(double valor) => 0.3 * valor;
}
```