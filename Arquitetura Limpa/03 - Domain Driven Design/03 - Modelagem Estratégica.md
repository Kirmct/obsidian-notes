	- A Modelagem Estratégica organiza a arquitetura de sistemas complexos, indetificando e delimitando contextos e subdomínios. 
	- Dividir o domínio em partes menores e autossuficientes (subdomínios).
	- Garantir a clareza de papéis e responsabilidade entre os subdomínios.

Recorte da aplicação para saber onde vamos "atacar" primeiro.
Pode ser difícil, saber se os recortes estão abrangendo muito, ou pouco, do que eles realmente deveriam abranger.

## Contexto Delimitado (Bounded Contexts)
	- Um limite lógico onde um modelo específico de domínio é aplicado, garantindo que um subdomínio tenha sua própria lógica e terminologia.
	- Importância:
		- Ajuda a evitar ambiguidades entre diferentes partes do sistema.
		- Define limites para cada equipe de desenvolvimento, permitindo que trabalhem de forma independente.

## Context Map
	- Um diagrama que ilustra como diferentes Contextos Delimitados se relacionam.
	- Tipos de Interação:
		- Parceria (Partnership): Colaboração próxima entre dois contextos.
		- Cliente-Fornecedor (Customer-Supplier): Um contexto depende de outro, definindo uma hierarquia de responsabilidades.
		- Serviço Compartilhado (Shared Kernel): Compartilhamento de uma parte do modelo entre contextos.

## Benefícios
	- Alinhamento de Domínios: Organiza o sistema para refletir a estrutura do negócio.
	- Redução de Ambiguidade: Limita o uso de terminologia confusa, pois cada contexto tem seu vocabulário específico.
	- Escalabilidade: Permite que equipes trabalhem em diferentes contextos sem dependências fortes.
	- Agilidade e Adaptabilidade: Facilita a implementação de mudanças em áreas específicas sem impacto significativo em outros contextos.

## Desafios
	- Dificuldade de Identificação de Subdomínios: Subdomínios mal definidos podem gerar confusão e retrabalho.
	- Sobrecarga de Documentação e Comunicação: A coordenação entre diferentes contextos e equipes pode se tornar complexa e dispendiosa.
	- Resistência Mal Geridas: Quando as interações entre contextos não são bem definidas, pode-se gerar um acoplamento forte, comprometendo a escalabilidade.