## Cenário
	Arquiteturas tradicionas frequentemente utilizam estruturas horizontais, com ccamadas dedidacas a diferentes funcionalidades, como interface, lógica de negócio e dados;
	Embora funcionais, essas abordagens frequentemente aumentam o acoplamento entre camadas, dificultando mudanças e escalabilidade em funcionalidades complexas.
## Conceito
	A Vertical SLice Arch reorganiza a aplicação em "fatias" verticais, onde cada fatia representa uma funcionalidade completa do sistema (ex: cadastro, pedidos, pagamento)
	Separar o código por funcionalidades em vez de camadas horizontais, concetrando todas as partes necessárias de uma funcionalidade em um únic módulo ou slice.

![[Pasted image 20241205103233.png]]

## Características
	Isolamento de funcionalidades: Cada fatia (slice) é independente e autônoma, contendo todas as camadas e dependências necessárias para executar uma função específica;
	Código centrado no comportamento: Em vez de dividir por tecnologia (ex: serviços, repositórios), a divisão é por comportamento, o que facilita localizar, modificar e testar funcionalidades específicas;
	Isolamento de dependências: Cada slice gerencia suas dependências de maneira isolada, o que reduz o impacto de mudanças em outras partes do sistema.
## Benefícos
	Escalabilidade de funcionalidades: Cada slice pode crescer e ser mantido de forma independente, facilitando a adaptação de novas necessidades;
	Alta coesão e baixa complexidade: Código relacionado a mesma funcionalidade fica concentrado, aumentando a coesão e reduzindo a complexidade do projeto;
	Testabilidade: Cada slice pode ser testado de forma independente, o que facilita a criação de testes de integração e end-to-end para funcionalidades específicas.

## Clean Arch + Vertical Slice Arch
	Semelhanças estruturais: Assim como o Vertical Slice Arch, o Clean Arch visa separar responsabilidades e reduzir acoplamento, mas organiza o código em camadas concêntricas.
	Influência na modularização: A ideia de independência e isolamento de cada slice ajudou a fortalecer o coneito de modularidade presente na Clean Arch, onde cada camada e componente deve ser o mais independente possível;
	Organização por casos de uso e funcionalidades: A vertical Slice Arch inspirou a criação de casos de uso separados na Clean Arch, ajudando a centralizar a lógica de negócios em unidades discretas e autônomas.

## Desafios
	Gerenciamento de dependências: Pode ser desafiador manter cada slice com as dependências certas sem criar redundâncias;
	Organização inicial: Definir os slices e o isolamento pode ser complexo em grandes sistemas e exige uma abordagem disciplinada para evitar vazamento de responsabilidades entre slices.