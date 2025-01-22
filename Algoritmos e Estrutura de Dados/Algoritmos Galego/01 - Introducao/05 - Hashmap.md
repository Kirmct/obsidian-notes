Em python é chamado de dictionary.
Armazena chave e valor.
Geralmente tem complexidade temporal de O(1).
Hash Function que faz isso.
No caso médio e melhor caso temos complexidade O(1).
No pior caso teríamos a complexidade de O(n) (ver collisions).

## Hash Function
Pega um input (chave) e faz alguma operação matemática, e com isto vai transformar essa key no slot do array onde está armazenado o valor que queremos.
Vai transformar a chave para uma posição no array, e nesta posição vai ser armazenada o item que queremos.

## Load Factor
Diferença de tamanho entre a quantidade de dados que temos e a estrutura de dados usada.
Um array com 10 posições com dois elementos preenchidos, teríamos um load factor de 20%, ou entao 0.2.
Assim se nossa Hash Function não for bem feita podem ocorrer colisões, 20% de chance de ocorrer.
Quando chegamos a 70% do array preenchido (em média), aumentaremos o tamanho da memória (geralmente dobrar) e então recalculamos o tamanho de memória alocada.

## Collisions
Onde dois elementos acabam sendo apontados para o mesmo endereço de memória. Podemos ter vários aproachs em relação a isso, mas até recentemente era usado a ideia de jogar para o próximo endereço de memória disponível. Esse fato pode fazer percorrer toda estrutura, fazendo a complexidade temporal ser de O(n).
Atualmente é usado o aproach de apontar para outra estrutura de dados quando isso acontece, um outro array ou linked list e nessa nova estrutura vão ser salvos as chaves e valores de cada um.