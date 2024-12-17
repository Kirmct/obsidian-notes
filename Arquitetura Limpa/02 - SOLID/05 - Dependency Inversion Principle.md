	O DIP afirma que módulos de alto nível não devem depender de módulos de baixo nível, mas sim de abstrações. Abstrações não devem depender de detalhes, os detalhes é que devem depender das abstrações.

## Benefícios
	Desacoplamento: Facilita a troca de implementações sem impactar o código de alto nível.
	Facilidade de Teste: Módulos podem ser testados isoladamente usando abstrações.

## Exemplo de má prática
Um módulo de alto nível que depende diretamente de uma classe concreta de baixo nível.
- Problema: A classe ServicoRelatorio depende diretamente da implementação concreta Repositorio. Isso dificulta a troca da implementação do repositório e aumenta o acoplamento.

```C#
public class Repositorio
{
	public void Salvar(string dados)
	{
		Console.WriteLine("Dados salvos no banco");
	}
}

public class ServicoRelatorio
{
	private Repositorio _repositorio;
	
	public ServicoRelatorio()
	{
		_repositorio = new Repositorio();
	}

	public void Proessar()
	{	
	_repositorio.Salvar("Relatorio");
	}
}
```

## Exemplo de boa prática
Agora dependemos da abstração, da interface, não da classe.
- Solução: A classe ServicoRelatorio depende da abstração IRepositorio, permitindo trocar a implementação concreta RepositorioBanco por qualquer outra que implemente IRepositorio.

```C#
public interface IRepositorio
{
	void Salvar(string dados); 
}

public class RepositorioBanco : IRepositorio
{
	public void Salvar(string dados)
	{
		Console.WriteLine("Dados salvos no banco");
	}
}

public class ServicoRelatorio
{
	private readonly IRepositorio _repositorio;
	
	public ServicoRelatorio(IRepositorio repositorio)
	{
		_repositorio = repositorio;
	}

	public void Proessar()
	{	
	_repositorio.Salvar("Relatorio");
	}
}
```

## Outro exemplo de má prática
```C#
public class EmailService
{
    public void Send() { }
}

//Em testes, nao teriamos como enviar um email fake
//ja que dependemos da implementação
public class UserService(EmailService service)
{

}
```

## Outro exemplo de boa prática
```C#
public interface IEmailService
{
    void Send();
}

public class EmailService : IEmailService
{
    public void Send()
    {
        Console.WriteLine("Enviando email");
    }
}

//criamos esta para fazer testes
public class FakeEmailService : IEmailService
{
    public void Send()
    {
        Console.WriteLine("Enviando email fake");
    }
}

//Assim podemos usar ambos os servicos de email
//Agora dependemos da abstração, não implementação
public class UserService(IEmailService emailService)
{}
```