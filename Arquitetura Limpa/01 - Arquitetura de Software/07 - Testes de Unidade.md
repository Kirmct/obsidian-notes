Tudo que fazemos relacionado a arquitetura tem como finalidade a possibilidade e facilitação de realizar testes, aumento da cobertura de testes;
## Testes de Unidade
	Verificam o comportamento de pequenas partes isoladas do código, como métodos ou funções, garantindo que cada parte funcione conforme o esperado;
	Rápidos, isolados e focados em validações específicas, facilitando a detecção de erros cedo no ciclo de desenvolvimento.
## Motivações
	Qualidade e Confiança: Testes de unidade garantem que a aplicação funcione como esperado, permitindo que novas funcionalidades sejam implementadas com confiança;
	Manutenção: Facilita a refatoração e evolução do código, pois erros são detectados rapidamente;
	Documentação Viva: Testes de unidade documentam a intenção do código, mostrando como cada parte deve se comportar;

## Conceitos
	Separação de Responsabilidades: Divide o sistema em camadas distintas, onde cada camada tem um propósito bem definido;
	Camadas da Arquitetura Limpa:
		Entidades: Contem regras de negócio, independente de detalhes técnicos;
		Casos de Uso (Application): Define a lógica de aplicação, orquestrando as entidades;
		Interfaces de Entrada/Saída (Interface Adapters): Faz a ponte entre o domínio e o mundo externo;
		Frameworks e Drivers: Camda mais externa, depende de detalhes técnicos (banco de dados, APIs).

## UT + CA
	O foco dos testes de unidade é principalmente nas camadas de domínio (Entidades) e aplicação (Casos de Uso), que não dependem de detalhes técnicos e são as mais suscetíveis a mudanças de regras de negócio.

## Benefícos
	Isolamento Completo: Cmadas de domínio e aplicação podem ser testadas de maneira isolada, pois não dependem de frameworks ou banco de dados;
	Evolução do Código: A arquitetura limpa favorece mudanças, e com testes de unidade, a refatoração é segura e contínua;
	Feedback Rápido: Detecta rapidamente problemas nas regras de negócio sem a necessidade de configurações complexas de infraestrutura.

## Boas Práticas
	Seguir o Princípio AAA (Arrange, Act, Assert): Estruturação dos testes para que sejam claros e legíveis;
	Evitar Dependência de Detalhes Técnicos: Uso mocks e stubs para simular dependências externas;
	Foco no Domínio: Priorize testar as regras de negócio e os casos de uso críticos;
	Facilidade de Leitura e Manutenção: Testes bem escritos facilitam a identificação de falhas e servem como documentação;

## Desafios e Soluções
	Desafios Comuns: Manter os testes relevantes e evitar testes frágeis que quebrem facilmente com pequenas mudanças;
	Soluções: Revisão periódica de testes, refatoração, e foco em testes de comportamento e não de implementação.

