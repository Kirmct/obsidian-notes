	DDD é uma abordagem de design de software que coloca o domínio do negócio no centro do desenvolvimento, buscando alinhar a solução técninca aos requisitos reais da área de negócios.
	Facilitar a comunicação entre técnicos e especialistas de domínio para que ambos compartilhem um entendimento claro e objetivo do problema a ser resolvido.

## Pilares
	Foco no Domínio: Conhecimento profundo do negócio;
	Colaboração Contínua: Entre desenvolvedores e especialistas no assunto;
	Linguagem Ubíqua: Um vocabulário comum para todos, evitando ruídos de comunicação.

## Conceitos Centrais
	Entidade e Objetos de Valor: Elementos que representam conceitos únicos e atributos do domínio;
	Agregados e Raiz do Agregado: A estrutura que garante consistência no estado das entidades;
	Serviços: Operações que não se encaixam diretamente nas entidades;
	Repositórios: Responsáveis pela persistência e recuperação das entidades de negócio.

## Modelagem
	- Estratégica (Visão Macro):
		Contexto Delimitado: Define limites claros para subdomínios;
		Mapa de Contexto: Visualiza a interação entre os contextos delimitados;
	- Tática (Visão Detalhada):
		Ferramentas específicas para criar e organizar o modelo, como agregados e objetos de valor.

## Benefícios
	Alinhamento entre software e negócio;
	Redução de ambiguidades e erros de interpretação;
	Evolução do software de forma sustentável.

## Desafios
	Complexidade Excessiva: Aplicar DDD em dom;inios simples podem introduzir complexidades desnecessárias e sobrecarga na estrutura do código.
	Custo de Implementação: DDD requer tempo e recursos para criar um modelo fiel ao domínio, o que pode ser um problema em projetos com orçamento ou prazos restritos;
	Curva de Aprendizado: A equipe precisa de um conhecimento aprofundado do negócio e da abordagem DDD, o que pode dificultar a adoção;
	Dependência de Colaboração: Sem colaboração próxima com especialistas de domínio, o modelo perde relevância, comprometendo a qualidade do software.