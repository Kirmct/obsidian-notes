## Pesquisa Binária
Imagine uma lista telefônica, nela buscamos pelo nome de Kirmct, como faríamos esta busca? Seria burrice ir desde a letra A, elemento por elemento, até chegarmos na letra K. O mais lógico seria abrir a lista o mais próximo possível da letra K, e em ordem alfabética tentar chegar o mais próximo possível do nome, até encontra-lo;
A busca binária funciona desta maneira, porém temos de ficar atentos a ordenação desta lista, caso ela esteja toda bagunçada este método não será eficaz.

	A pesquisa binária se baseia na divisão pela metade do array/lista para que desta maneira a quantidade de execuções seja inferior a uma busca sequencial;
	Enquanto a busca sequencial percorre todos os items da lista para achar o resultado, temos um tempo de excecução de On;
	Já na busca binária, usando o método de dividir o espaço percorrido, no pior dos cenários temos uma execução de Log N;
```C
#include <stdio.h>
#define ARRAY_SIZE(arr) (sizeof(arr) / sizeof((arr)[0])) 
int binarySearch(int arr[], int size, int value)
{
    int begin = 0, end = size - 1; 
    //enquanto pudermos percorrer a lista
    while (begin <= end)
    {
    //o meio sempre arredonda para baixo
        int mid = (begin + end) / 2;
        int guess = arr[mid]; 
        
        if (guess == value){
            return mid;
        }  
		//se o valor chutado for maior que o buscado, entao devemos buscar         //por valores menores, assim diminuindo o final da lista
		//caso contrário, aumentamos o início da mesma
        if (guess > value){
            end = mid - 1;
        }else{
            begin = mid + 1;
        }
    } 
    return -1;
} 

int main(){
    int arr[4] = {1, 3, 6, 12};
    int size = ARRAY_SIZE(arr);  
    int result = binarySearch(arr, size, 12);  
    if (result == -1){
        printf("The element doesnt exists in this array!");
    }else{
        printf("The elemente positions is: %d", result);
    } 
    return 0;
}
```


## Notação Big O
Diz o quão rápido é um algoritmo.
Os tempos de execução de algoritmos crescem em taxas diferentes.
Big O não fornece o tempo em segundos, etc, ele permite que você compara o número de operações necessárias para realizar;
Informa o quão rapidamente ele cresce.
**O Big-O sempre leva em consideração o pior caso!**, tendo em vista que este é sempre a garantia do máximo número de operações. 
Temos também o caso médio, mas veremos mais a frente.
Os tempos mais comuns são (mais rápido para mais lento):

	O(log n) -> tempo logarítimico, ex: pesquisa binária.
	O(n) -> tempo linear, ex: pesquisa simples.
	O(n * log n) -> ex: algoritimo rápido de ordenação, como quicksort.
	O(n^2) -> ex: algoritimo lento de ordenação, como o por seleção.
	O(n!) -> ex: algoritimo bastante lento, como caixeiro viajante.