Time Complexity:
- Best Case: O(n)
- Worst Case: O(n^2)
Space Complexity: O(1)

## Vantagens
Complexidade temporal boa.
Não usa nenhuma estrutura de dados extra. Só troca os elementos.

## Implementação
```C#
public int[] Bubble(int[] nums)
{
    var size = nums.Length;

    for (int i = 0; i < size; i++)
    {
        for (int j = 0; j < size - 1 - i; j++)
        {
            if (nums[j] > nums[j + 1])
            {
                var temp = nums[j];
                nums[j] = nums[j + 1];
                nums[j + 1] = temp;
            }
        }
    }

    return nums;
}
```
