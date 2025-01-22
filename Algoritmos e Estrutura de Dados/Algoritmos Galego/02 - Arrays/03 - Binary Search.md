Não existe uma estrutura de dados específicas.
Só funciona se essa estrutura estiver ordenada.
Temporal: O(Log n)
Espacial: O(1)

## No array
Apontamos para o meio do array, e verificamos se está dentro do que esperamos, se não for, vemos se é maior ou menos e descartamos o resto, até chegar ao resultado.
Podemos fazer usando 3 ponteiros, usando um para salvar o fim, o inicio e o meio, e assim poder trabalhar no que desejamos.
```C#
    public static int Search(int[] arr, int target)
    {
        int left = 0, right = arr.Length - 1, mid = (arr.Length - 1) / 2;

        while (left <= right)
        {
            mid = (right + left) / 2;

            if (arr[mid] == target)
                return mid;
            else if (arr[mid] < target)
                left = mid + 1;
            else
                right = mid - 1;
        }

        return -1;
    }
```