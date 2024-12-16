## Recursão
Recursão é quando fazemos chamadas para a mesma função, na tentativa de tornar o código mais claro.
Não há nenhum benefício em usar recursão.
Loops algumas vezes podem ter melhor desempenho que funções recursivas.

### Caso Base e Caso Recursivo
Como a função recursiva chama a si mesma, pode ocorrer, erroneamente, de entrarmos em um loop infinito.
Quando estivermos escrevendo uma função recursiva SEMPRE devemos informar quando esta função irá parar.
A função recursiva tem duas partes:
- Caso Base
- Caso Recursivo
#### Caso Recursivo
É quando a função chama a si mesma, gerando assim a recursividade.

#### Caso Base
É quando a função não chama a si mesma, desta forma a função não entra em um loop infinito.


## Pilha
Imaginemos uma pilha de livros, nós sempre adicionaremos livros no topo, e sempre retiramos os livros pelo topo.

## Pilha de chamada (call stack)
O computador usa uma pilha interna, chamada pilha de chamada.
Cada vez que uma função é chamada seu computador salva na memória. 
Caso tenha uma função dentro da outra, ele irá executar parte da primeira, até entrar na segunda, criando assim um epilhamento de funções para seguir. Isto seria a pilha de chamadas.
Quando a função mais interna é finalizada, esta é retirada do topo da pilha, e logo em seguida a função mais interna é executada, quando não houver mais comandos para serem feitos acaba o processamento.

## Pilha de chamadas e Recursão
A recursão utiliza desta pilha de chamadas para realizar seu objetivo.
Pilha é bom, porém existe um custo: 
	Salvar todas estas informações pode ocupar muita memória.
Quando a pilha está muito cheia, seu computador está salvando muitas informações para muitas chamada, podendo ocorrer um erro de estouro de memória (Stack Overflow).
Para esta situação podemos:
* Reescrever o código usando loops;
* Utilizar tail recursion (recursão de calda).