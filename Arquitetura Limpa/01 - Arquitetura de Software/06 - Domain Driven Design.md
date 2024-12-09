Para ter um arquitetura limpa não é necessário ter o DDD;
O DDD é uma forma de desenvolver, não é uma arquitetura, não precisa dele para implementar uma arquitetura limpa.
Porém ajuda muito, principalmente na área de testes.

## O que é Domain Driven Design
	É um conjunto de princípios e padrões para o desenvolvimento de software, focado na resolução de domínio com uma colaboração intensa entre equipe técninca e especialistas no negócio;
	Construir um sistema alinhados ao "Domínio" do negócio, criando uma linguatem comum para evitar mal entendimentos e garantir que todos entendam o sistema da mesma maneira;
## Por que utilizar?
	Alinhamento com o negócio: Foca na resolução de problemas reais e específicos de negócio;
	Escalabilidade do Conhecimento: Facilita a comunicação e colaboração entre equipe técnica e não técnica;
	Manutenbilidade: Promove um código mais organizado, facilitando mudanças ao longo do tempo;

## Conceitos
	Domínio: O conjunto de regras, lógica e comportamento da área de negócio;
	Linguagem Obíqua: Criação de uma linguagem comum entre o time, sem jargões técnicos, que todos possam entender;
	Modelagem do domínio: Mapeamento das entidades, eventos e comportamnetos do negócio para o código.
	Bounded Context: contextos delimitados, Separação do sistema em áreas específicas, onde cada contexto possui sua própria definição de termos e regras;
	Entidades: Objetos com identidade única;
	Objetos de valor: Objetos imutáveis que representam conceitos do domínio, sem identidade própria;
	Agregados: Agupamentos de entidades e Objetos de Valor que garantem consistência.
	Serviços de Domínio: Contêm lógica de negóci que não se encaixa diretamente em uma entidade.
	Repositórios: Interface para o armazenamento e recuperação de agregados, geralmente usados para conectar o sistema ao banco de dados.

## Benefícios
	Facilidade de Manutenção: Com o sistema mais organizado, as alterações são realizadas de forma mais intuitiva;
	Colaboração Ampliada: A linguagem comum facilita a comunicação e colaboração com os especialistas do negócios;
	Evolução do Sistema: Permite a expansão de funcionalidades sem perder o controle sobre o sistema.

## Desafios
	Complexidade: Pode adicionar camadas e conceitos que são desnecessários em sistemas pequenos;
	Curva de aprendizado: Requer compreensão dos conceitos e adaptação por parte do time;
	Tempo Inicial: O processo de modelagem e criação da linguagem ubíqua pode ser demorado.

### DDD + CA
	DDD: Define a estrutura do domínio do negócio e facilita o entendimento da lógica de negócios, com ênfase no alinhamento e na colaboração entre o time técnico e os especialistas de negócio;
	Clean Architecture: Estrutura a aplicação em camadas, isolando dependências e garantindo que a lógica seja independente de frameworks, UI, bancos de dados e outros detalhes externos.

### Integração (DDD + CA)
	Camada de Domínio (Core): DDD fornece os modelos de domínio, entidades, objetos de valor e agregados que compõem essa camada, permitindo que a lógica de negócio seja pura e livre de dependências externas;
	Use cases e Aplicação: Clean Arch introduz camadas de uso de caso que coordenam os fluxos de trabalho, permitindo a implementação de serviços de domínio e aplicação de políticas de negócios descritas pelo DDD.
	Adaptadores e Infraestrutura: Clean Arch usa adptadores para conectar o domínio aos serviços externos, enquanto DDD define interfaces de repositórios e serviços, mantendo o domínio independente da infraestrutura.

### Benefícios (DDD + CA)
	Isolamento e Testabilidade: Domínio independente facilita os testes unitários, com casos de uso sendo testados de forma isolada;
	Flexibilidade: Mudanças na UI, banco de dados ou frameworks não afetam a lógica central;
	Simplicidade e Escalabilidade: Domínio estruturado e limpo, com alto potencial de evolução e sustentabilidade a longo prazo.
