	Em arquiteturas tradicionais a lógica de negócio frequentemente depende de frameworks, camadas de UI e bancos de dados, criando alto acoplamento e dificultando testes e manutenção;
	Esse cenário gerou a demanda por uma arquitetura que mantivesse a lógidaca de negocios independente de implementações externas.
## Conceitos
	Proposta por Robert C Martin (Uncle Bob), a Clean Arch visa desacoplar totalmente a lógica de negócio das dependências externas, promovendo alta modularidade, flexibilidade e testabilidade;
	Manter a lógica de negócio (núcleo) intocável organizada em camadas que garantem que cada parte da aplicação esteja em um local previsível e claro;
## Camadas
	Entities (entidades): Representam as regras de negócio essencais e independentes de qualquer implementação de infraestrutura ou framework;
	Use Cases (Casos de Uso): Coordenam e aplicam as regras de negócio para resolver problemas específicos;
		Esta camada conecta a aplicação ao mundo externo sem se acoplar a ele;
	Interface Adapters (Adaptadores de Interface): traduzem dados entre os casos de uso e interfaces externas, como banco de dados, frameworks, ou UI;
	Frameworks & Drivers: A camada mais externa, que engloba detalhes de implementação, incluindo frameworks, bibliotecas e serviços externos; 

![[Pasted image 20241205093630.png]]

## Princípios
	Dependências direcionadas para o núcleo: Cada camada só pode depender de camadas mais internas, nunca o contrário, o que protege a lógica central de mudanças nas interfaces externas;
	Independência de frameworks: A aplicação não depende diretamente de frameworks, permitindo que mudançass nessas tecnologias sejam feitas sem afetar o núcleo;
	Alta testabilidade e facilidade de manutenção: Com as dependêncas externas isolada, fica mais fácil testar, manter e evouir o sistema ao longo do tempo.

## Onion Arch VS Clean Arch
	Assim como a Onion Arch, a Clean Arch utiliza camadas concêntricas para proteger a lógica de negócio de detalhes externos, mas vai além ao definir claramente as responsabilidades de cada camada;
	O conceito de casos de uso é uma contribuição exclusiva da Clean Arch, destacando a importância de um nível intermediário para gerenciar a interação entre lógica de negócio e interfaces externas.

## Benefícos
	Flexibilidade e modularidade: A aplicação é mais fácil de modificar e adaptar a novas demandas e tecnologias;
	Independência tecnológica: mudanças em frameworks, banco de dados ou UI não afetam a lógica de negócio central;
	Facilidade na criação de testes automatizados: A separação clara entre lógica de negócio e infraestrutura facilita a implementação de testes unitários e de integração;