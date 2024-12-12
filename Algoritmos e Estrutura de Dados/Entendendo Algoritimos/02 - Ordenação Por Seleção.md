## Como funciona a Memória
Imaginemos a memória do computador como uma sala de cinema, temos vários lugares, que podem estar, ou não, ocupados por pessoas, de várias maneiras possíveis. 
Nunca que uma sala de cinema vai alocar mais pessoas que assentos. Esta lógica funciona também para a memória do computador.
No computador temos vários espaços destinados a guardar algo, quando pedimos um destes espaços ele nos fornece um endereço de memória, este endereço aponta para o local onde a informação ficará armazenada.
## Arrays
Usar um array significa que você precisará destes espaços de memória de maneira sequencial. Como por exemplo, quando vai ao cinema com os amigos, queremos sentar ao lado, então reservamos N cadeiras para acomodar todos. O array funciona desta maneira, decidimos o tamanho primeiro, e então solicitamos, de maneira sequencial, slots de memória ao computador.

### Inserção 
Voltando ao cinema, caso um amigo a mais chegue, e nós querermos sentar próximos, e não tiver cadeira onde estamos, teremos que fazer uma mudança total de lugares e buscar um onde possamos todos sentar próximos.
Este também é um problema do array, caso criamos um inicialmente com valor N, porém no futuro precisarmos de mais espaço, pode ser que não seja possível alocar de maneira sequencial, então teríamos que mover todos os elementos para um local onde tenha disponibilidade, isto se existir tal local. Podemos tentar prever isso alocando mais memória que precisamos, porém isto pode ser um grande desperdício. Já que se estiver reservada para um array, nada mais poderá usá-la.
### Busca
Um array tem como vantagem a rapidez de busca, tendo em vista que os elementos estão alocados de maneira sequencial, logo fica fácil identificar, através de índices, qual elemento está e determinada posição.

### Inserção no Meio
Temos um problema na inserção no meio de um array, além de podermos ter o problema de alocamento de memória, também teríamos a necessidade de mover todos os próximos elementos uma posição a frente, para aí sim podermos alocar a informação desejada.

### Deleção
A deleção no final do array não é algo tão problemático, na deleção nunca teremos o problema de falta de slots de memória, porém a deleção em elementos no meio dele gera o mesmo problema da inserção no meio, o problema relacionado a mover todos os elementos para que o array continue alocado sequencialmente.

### Notação
	Leitura: O (1)
	Inserção: O (n)
	Deleção: O (n)

## Listas Encadeadas
As listas encadeada se parecem com arrays, no quesito funcionalidade, porém elas se diferenciam quando estas não precisam estar alocadas sequencialmente, elas podem estar alocadas em qualquer local de memória.
E como isto é possível? já que as listas não estão alocadas sequencialmente, elas usam um ponteiro, que basicamente é um valor que faz referência ao próximo elemento da lista.  Assim, não precisam estar uma ao lado da outra, já que cada elemento sabe a posição do próximo valor.

### Inserção
Nas listas encadeadas não temos os mesmo problema de inserção dos arrays, já que estas independem da localização, então sua inserção é bem rápida, fazendo somente o elemento anterior apontar para o que está sendo inserido agora.

### Busca
A busca pode ser um problema para as listas encadeadas, porém somente em buscas específicas. Diferentes dos arrays onde podemos buscar por um índice específico, as listas não tem essa funcionalidade, então ao buscar um item específico só será possível se formos percorrer cada elemento da lista.
Mas veja bem, este problema se dá somente em buscas específicas, caso queira retornar todos os valores da lista se torna uma operação comum.

### Inserção no meio
Não temos problemas algum ao inserir um elemento em qualquer posição da lista, não precisamos mover todos os outros como no array. A única coisa que precisamos é fazer seu anterior apontar para esse elemento, e esse elemento apontar para o próximo.

### Deleção
A deleção em listar também é uma funcionalidade simples, podemos somente apagar o valor, e fazer com que o seu anterior aponte para o elemento que este estava apontando.

### Notação
	Leitura: O (n)
	Inserção: O (1)
	Deleção: O (1)

## Selection Sort
Temos diversos algoritmos de ordenação, um deles é a ordenação por seleção. Onde nós basicamente percorremos cada elemento da lista, vemos qual é o menor e trocamos de posição.
Este tipo de abordagem nos faz percorrer cada elemento N vezes, tornando assim seu tempo de execução mais demorado.

	O (n^2)

### Código em C
````C
#include <stdio.h>
#define ARRAY_SIZE(arr) (sizeof(arr) / sizeof((arr)[0])) 
void selectionSort(int arr[], int size){
    // teremos que percorrer cada elemento do array
    for (int i = 0; i < size; i++)
    {
	    //adotamos o valor menor o elemento da vez
        int lowersIndex = i;  
        //percorremos o restante do array 
        for (int j = i + 1; j < size; j++)
        {
	        //se o indice do valor atual for menor que o valor do indice do menor, trocamos o indice do menor
            if (arr [j] < arr[lowersIndex])
            {
                lowersIndex = j;
            }            
        }  
        //fazemos o swap dos valores
        int aux = arr[i];
        arr[i] = arr[lowersIndex];
        arr[lowersIndex] = aux;
    }
}  
int main(){
    int arr[] = { 1, 4, 8, 3 };
    int size = ARRAY_SIZE(arr);  
    
    printf("Original Array: ");
    for (int i = 0; i < size; i++)
    {
        printf("%d ", arr[i]);
    }
    // ordenando
    selectionSort(arr, size);  
    printf("\nOrdered Array: ");
    for (int i = 0; i < size; i++)
    {
        printf("%d ", arr[i]);
    }
    return 0;
}
```