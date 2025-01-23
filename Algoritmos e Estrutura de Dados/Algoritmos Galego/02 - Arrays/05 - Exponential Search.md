Usa binary search como parte da busca
Tem mesma complexidade
Temporal: O(Log n) 
Espaço: O(1)
Se array for muito grande pode ser uma boa solução.
Ela meio que dobra a busca em cada iteração.
Vamos encontrar o sub-array e dentro dele vamo fazer a binary search
```C#
public static int Search(int[] arr, int target)
{
    if (arr[0] == target) return 0;
    int size = arr.Length, right = 1;

    while (right < size && arr[right] < target)
    {
        right *= 2;//sempre dobramos para maximizar o sub-array
    }
    if (right < size && arr[right] == target) //caso tenha achado
        return right;

    int left = right / 2;
    //o right pode ter passado do tamanho do array, se tiver passado
    //teremos que passar o tamanho, caso n faça isso
    //dara erro de outofbalance
    return BinarySearch(arr, target, left, Math.Min(right, size - 1));
}

public static int BinarySearch(int[] arr, int target, int left, int right)
{
    int mid = 0;

    while (left <= right)
    {
        mid = left + (right - left) / 2;

        if (arr[mid] == target)
            return mid;
        else if (arr[mid] > target)
            right = mid - 1;
        else
            left = mid + 1;

    }
    return -1;
}
```