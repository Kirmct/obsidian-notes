## Dividir para Conquistar (DC)
Funciona por meio da divisão do problema em problemas menores.
Temos que diminuir o problema até encontrar o caso-base, após encontrar devemos trabalhar em cima deste.
- Dica: Quando a recursão envolver um array, muitas da vezes o caso-base será um array vazio ou array de 1 elemento.

## Quicksort
É um algoritmo de ordenação muito rápido, que usa como base a estratégia DC.
Passos:
- Escolha um pivô;
- Encontre elementos menores e maiores que ele;
- Menores na esquerda e maiores na direita;
- Faça o mesmo para ambos os lados;
- Fazer até chegar no caso base;

## Notação Big O revisada
	O quicksort é único, pois sua velocidade depende do pivô escolhido.
Na sua pior situação ele tem tempo de execução O(n^2);
No caso médio tem tempo de execução O(n log n);

### MergeSort VS QuickSort
	MergeSort sempre tem notação padrao O(n log n).
Geralmente as constantes na notação Big O são desconsideradas, pois estas não são importantes em algoritmos com tempo de etapas diferentes.
Como por exemplo a pesquisa simples com O(n) e a pesquisa binária com O(log n), caso a simples tenha tempo de execução de 10 milissegundos e a binária de 1 segundo, em casos piores a binária sempre vai ser mais rápido, como em um processo com 4 bilhões de registros:
- Simples -> 10ms X 4 bilhoes = 463 dias
- Binaria -> 1s X 32 (log n) = 32 segundos

	O quicksort comparado ao mergesorte é um exemplo disto. Já que o quicksort tem uma constante de execução menor que o mergesort. Apesar de ambos terem tempo de execução O(n log n), o quicksort tem vantagem pois sua constante é menor.


