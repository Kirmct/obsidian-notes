Falar como o algoritmo escala de acordo com o input (entrada).
Vai dizer quão bem ou quão mal o algoritmo escala dado um tamanho de input.
Porém temos que levar em conta que há casos em que O(n) pode ser pior que O(n^2), mas veremos isso quando falarmos de Análise Assintótica.
Usado para medir a complexidade temporal e complexidade espacial.

- Complexidade Temporal -> Quanto tempo ele leva para executar (Runtime).
- Complexidade Espacial -> Quanto de memória adicional precisa alocar de novo espaço, tamanho.

## Principais Big O Notations
Sempre (quase) consideramos o pior caso.
- O(1): Tempo constante, memória constante. Mesmo tempo de execução, mesma quantidade de memória alocada. 
- O(Log n): Conforme o input aumenta rápido, o tempo de execução não aumenta tão rápido. Binary Search é um exemplo. Conforme você aumenta o input exponencialmente, o tempo aumenta linearmente. Dobrar o input não dobra o tempo de execução.
- O(n): Tempo constante, escala na mesma medida que o input aumenta.
- O(n Log n): Boa parte dos algoritmos de Sorting, e Divide and Conquer. Complexidade espacial meio raro.
- O(n^2): Quando temos um loop dentro de outro. Para cada item ele checa todos outros items.
- O(2^n)
- O(Raiz n) -> Exponencial Search
-  O(N!)
