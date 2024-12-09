## Ports and Adapters
	A arquitetura Ports and Adapters isola a lógica central da aplicação de detalhes externos, como banco de dados e interfaces;
	"Ports" são interfaces para interações, e "Adapters" conectam sistemas externos, trazendo flexibilidade e facilidade nos testes.
Buscavam abstração, barreiras para facilitar comunicação e acessos
![[Pasted image 20241203163927.png]]
## Hexagonal Architecture
	A Arquitetura Hexagonal isola o núcleo da aplicação dos elementos externos, como banco de dados e interfaces;
	Seu design permite conectar diferentes "portas" (interfaces) e "adpatadores", garantindo flexibilidade e facilidade para testar e evoluir a aplicação;

![[Pasted image 20241203164506.png]]
Core Domain -> As regras da nossa aplicação;
Domain -> compõe o principal;
Por fora temos a aplicação.
## Onion Architecture
	Em projetos complexos, arquiteturas tradicionais, como baseadas em camadas (Layered Architecture), frequentemente sofriam com alto acomplamento e dependências difíceis de gerenciar;
	Essas depedências dificultavam a testabilidade, manutenção e escalabilidade do sistema, criando a necessidade de uma nova abordagem.
	Foi proposta para resolver o problema da dependência direta entre a lógica de negócio e infraestruturas externas (como bando de dados e frameworks);
	Apresenta um modelo em camadas onde as dependências fluem de fora para dentro, protegendo o núcleo de regras de negócio de influências externas;
	Cada camada deve depender apenas de camadas internas, garantindo que o coração da aplicação (a lógica de negócio) seja protegido de mudanças e que funcionalidades externas possam ser adicionadas sem afetar o núcleo.


### Componentes da Onion Arch
	**Core (núcleo)**: Representa as **entidades de domínio** e **serviços de domínio** (a lógica de negócio central). Esta camada não conhece detalhes externos;
	**Application Services**: Provê as funcionalidades que a aplicação expões ao mundo externo, organizando o uso das regras de negócio;
	**Infrastructure e Interfaces Externas**: Interagem com sistemas externos, como bancos de dados, interfaces de usuário e APIs. Depende de interfaces e abstrações criadas nas camadas internas.
### Pontos Fortes
	Isolamento de dependências externas: A lógica central fica isolada, permitindo testes mais fáceis e maior estabilidade;
	Alta testabilidade e manutenção: As dependências sendo direcionadas para o núcleo facilitam a substituição e adaptação das interfaces externas;
	Facilidade na evolução: Com camadas bem definidas e independentes, o sistema se torna mais modular e adaptável as mudanças.
### Influência no CA
	O Clean Architecture adota e expande o princípio de dependências orientadas para o núcleo, adicionando camdas adicionais como Use Cases e Frameworks;
	Assim como na Onion Architecture, o Clean Architecture visa minimizar dependências de frameworks e tecnologias externas, mantendo o foco na lógica de negócio;
	O Clean Arch leva os princípios da Onion Arch a um novo nível, facilitando a criação de aplicações ainda mais robustas e de fácil manutenção.
	
![[Pasted image 20241204100925.png]]