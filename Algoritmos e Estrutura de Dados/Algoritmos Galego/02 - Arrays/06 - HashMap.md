Uma das mais versáteis estrutura de dados que temos.
Como exemplo veremos o exercício de First Unique Character in a String
Pois podemos resolver com HashMap, armazenando o valor da chave (letra), e um array, contendo a primeira posição que aparece e quantas vezes aparece o tal elemento.
```C#
public static int GetFirstUniqueCharacterInAString(string s)
{
    var chars = s.ToArray();
    var result = new Dictionary<char, int[]>();

    for (var i = 0; i < chars.Length; i++)
    {
        if (!result.ContainsKey(chars[i]))
            result.Add(chars[i], [i, 1]);
        else
            result[chars[i]][1]++;
    }

    foreach (var item in result.Values)
    {
        if (item[1] == 1)
            return item[0];
    }

    return -1;
}
```

Outro exemplo, resolvendo o problema de TwoSum usando HashMap
```C#
public static int[] TwoSum(int[] nums, int target)
{
    var result = new Dictionary<int, int>();

    for (int i = 0; i < nums.Length; i++)
    {
        var complement = target - nums[i];

        //ver se tem o complemento no map
        if (result.ContainsKey(complement))
            return [result[complement], i];

        //se nao tiver esse valor adicionar
        if (!result.ContainsKey(nums[i]))
            result.Add(nums[i], i);
    }

    return [];
}
```