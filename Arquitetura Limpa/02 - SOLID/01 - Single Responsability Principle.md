	O SRP afirma que uma classe deve ter apenas uma responsabilidade e uma razão para mudar.
## Benefícios
	Manutenção facilitada: Classes com uma responsabilidade específica são mais fácies de entender e modificar.
	Reutilização e Testes: Classes focadas em uma única responsabilidade são mais reutilizáveis e fáceus de testar.
	Organização e Clareza: Cada classe tem um propósito claro;
	Redução de Acoplamento: Cada classe pode ser alterada sem impacter outras partes desnecessariamente.
	
**Exemplo de Má Prática:** 

	Uma classe que lida com lógica de negócios e também se encarrega de salvar dados no banco.

## SRP - Mau Exemplo
	A classe Relatorio tem duas responsabilidades - gerar relatório e salvá-lo. Isso viola o SRP.
	
```C#
	public class Relatorio
	{
		public string Conteudo { get; set; }

		public void GerarRelatorio()
		{
			// gerar relatorio - lógica de negócios
			Console.WriteLine("Gerando relatorio...");
		}
		
		public void SalvarRelatorio()
		{
			// salvar relatorio - lógica de persistencia dadods
			Console.WriteLine("Salvando relatorio...");
		}
	}
```


## SRP - Bom Exemplo
	Divida as responsabilidades em duas classes especializadas;
	A classe GeradorRelatorio agora foca apenas em gerar o relatório, enquanto RelatorioPersistencia cuida da persistencia.
```C#
	public class GerarRelatorio
	{
		public void Gerar()
		{
			// gerar relatorio
			Console.WriteLine("Gerando relatorio...");
		}		
	}

	public class RelatorioPersistencia
	{			
		public void SalvarRelatorio(string Conteudo)
		{
			// salvar relatorio
			Console.WriteLine("Salvando relatorio...");
		}	
	}
```