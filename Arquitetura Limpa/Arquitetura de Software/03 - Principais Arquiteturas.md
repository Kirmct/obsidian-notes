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
	Cada camada deve depender apenas de camadas internas, garantindo que o coração da aplicação
asdasd