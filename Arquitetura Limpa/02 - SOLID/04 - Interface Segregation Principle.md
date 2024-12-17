	O ISP afirma que uma interface não deve forçar classes a implementar métodos que elas não utilizam.

## Benefícios
	Flexibilidade e Clareza: Interfaces específicas evitam que classes implementem métodos desnecessários.
	Manutenção e Testes Fáceis: Classes ficam mais fáceis de manter e testar, pois têm interfaces enxutas e focadas.

## Exemplo de má prática
Interfaces grandes que obrigam classes a implementar métodos irrelevantes para elas.

```C#
public interface IAcoesAnimal
{
	void Comer();
	void Nadar();
	void Voar();
}

public class Cachorro : IAcoesAnimal
{
	public void Comer => Console.WriteLine("Cachorro comendo.");
	public void Nadar => Console.WriteLine("Cachorro nadando.");
	//Problema
	public void Voar => throw new NotImplementedException();
}
```
- Problema: Cachorro é forçado a implementar Voar(), o que não faz sentido. Isso viola o ISP, pois a interface obriga a implementação de métodos que a classe não precisa.

## Exemplo de boa prática
- Solução: As interfaces IComer, INadar, e IVoar são focadas e permitem que cada classe implemente apenas as interfaces que fazem sentido para ela.
```C#
public interface IComer
{
	void Comer();
}

public interface INadar
{
	void Nadar();
}

public interface IVoar
{
	void Voar();
}

public class Cachorro : IComer, INadar
{
	public void Comer => Console.WriteLine("Cachorro comendo.");
	public void Nadar => Console.WriteLine("Cachorro nadando.");
}

public class Passaro: IComer, IVoar
{
	public void Comer => Console.WriteLine("Passaro comendo.");
	public void Nadar => Console.WriteLine("Passaro nadando.");
}
```

## Outro exemplo de má prática
Empregados terceirizados não recebem benefícios, portanto a interface faz com que a classe tenha métodos não utilizados.
```C#
public interface IEmployee
{
    string Name { get; set; }

    void CalculateSalary();
    void CalculateBenefits();
}

public class FullTimeEmployee : IEmployee
{
    public string Name { get; set; }

    public void CalculateBenefits()
        => Console.WriteLine("Calculando Salário");
   

    public void CalculateSalary()        
        => Console.WriteLine("Calculando Benefícios");
}

public class ContractEmployee : IEmployee
{
    public string Name { get; set; }

    public void CalculateBenefits()
        => Console.WriteLine("Calculando Salário");

    public void CalculateSalary()
        => throw new NotImplementedException();
}
```

## Outro exemplo de boa prática
Assim não somos obrigados a implementar um método que não será utilizado na classe;
```C#
public interface ISalaryCalculator
{
    void CalculateSalary();
}

public interface IBenefitCalculator
{
    void CalculateBenefits();
}

public interface IEmployee
{
    string Name { get; set; }
}

public class FullTimeEmployee : IEmployee, ISalaryCalculator, IBenefitCalculator
{
    public string Name { get; set; }

    public void CalculateBenefits()
        => Console.WriteLine("Calculando Benefícios");

    public void CalculateSalary()
        => Console.WriteLine("Calculando Salário");
}

public class ContractEmployee : IEmployee, ISalaryCalculator
{
    public string Name { get; set; }

    public void CalculateSalary()
        => Console.WriteLine("Calculando Salário");
}
```