	O LSP afirma que objetos de uma classe derivada devem poder substituir objetos de sua classe base sem alterar a funcionalidade do programa.

## Benefícios
	Consistência e Confiabilidade: Classes derivadas devem manter o comportamento esperado da classe base.
	Polimorfismo Seguro: Permite que as substituições sejam feitas sem quebrar o código.

## Exemplo de má prática
	Classes derivadas que alteram ou invalidam funcionalidades da classe base.
- Problema: a classe quadrado tenta herdar Retângulo, mas o comportamento de Largura e Altura é alterado, quebrando a substituição segura.
```C#
 public class Retangulo
 {
     public virtual double Largura { get; set; }
     public virtual double Altura { get; set; }

     public double Area()
         => Largura * Altura;
 }

 public class Quadrado : Retangulo
 {
     public override double Largura 
     {
         set { base.Largura = base.Altura = value; }
     }

     public override double Altura
     {
         set { base.Largura = base.Altura = value; }
     }
 }
```

## LSP - Bom exemplo
	Retangulo e Quadrado agora herdam da classe Forma de maneira independente. Assim, Quadrado e Retangulo podem ser utilizados substituindo Forma sem impactar o comportamento.
```C#
public abstract class Forma
{
    public abstract double Area();
}

public class Retangulo : Forma
{
    public double Largura { get; set; }
    public double Altura { get; set; }
    public override double Area()
     => Largura * Altura;
}

public class Quadrado : Forma
{
    public double Lado { get; set; }
    public override double Area()
     => Lado * Lado;
}
```

## Outro exemplo ruim
Aqui SavingsAccount ele não consegue substituir o BankAccount, ele precisa sobrescrever o comportamento do pai por algum motivo (no caso a regra de negócios no saque).
```C#
public class BankAccount
{

    public virtual void Withdraw(decimal amount)
    {
        Console.WriteLine($"Withdraw: {amount}");
    }
}

public class SavingsAccount : BankAccount
{
    public decimal Balance { get; set; }


    public override void Withdraw(decimal amount)
    {
        if (Balance < amount) 
            throw new Exception("Insufficient balance");

        Balance -= amount;
        Console.WriteLine($"Withdraw: {amount}");

    }
}
```

## Outro exemplo bom
Aqui não alteramos o comportamento da classe base, isto porque a classe base não tem comportamento. Ela esta delegando o comportamento para as demais.
```C#
public abstract class BankAccount
{
    public decimal Balance { get; protected set; }
    public abstract void Withdraw(decimal amount);
}

public class SavingsAccount : BankAccount
{
    public override void Withdraw(decimal amount)
    {
        if (Balance < amount)
            throw new Exception("Insufficient balance");

        Balance -= amount;
        Console.WriteLine($"Withdraw: {amount}");
    }
}

public class CheckingAccount : BankAccount
{
    public override void Withdraw(decimal amount)
    {
        Console.WriteLine($"Withdraw: {amount}");
    }
}
```

