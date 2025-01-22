Consiste em inicializar dois ponteiros (índices), um no começo e outro no fim, e manipular esses ponteiros para não termos que adicionar espaços adicionais na memória.
A vantagem se dá em utilizar os ponteiros para acessar os dados, não precisando alocar mais espaço em memória para tal.
Como exemplo vamos utilizar o problema Reverse Words in a String III, disponível em https://leetcode.com/problems/reverse-words-in-a-string-iii/description/
```C#
// versao com complexidade melhorada
//versao com while
public static string ReverseWordsInAStringIIIV3(string s)
{
	char[] chars = s.ToCharArray();
	int left = 0, right = 0;

	while (right < chars.Length)
	{
		if (chars[right] != ' ')
			right++;
		else
		{
			Reverse(chars, left, right - 1);
			right++;
			left = right;
		}
	}

	Reverse(chars, left, right - 1);            

	return new string(chars);
}

//versao com for
public static string ReverseWordsInAStringIIIV2(string s)
{
    if (string.IsNullOrWhiteSpace(s)) return s;

    char[] chars = s.ToCharArray();
    int n = chars.Length;

    int start = 0;
    for (int end = 0; end <= n; end++)
    {
        if (end == n || chars[end] == ' ')
        {
            Reverse(chars, start, end - 1); 
            start = end + 1; 
        }
    }

    return new string(chars);
}

private static void Reverse(char[] data, int left, int right)
{
    while (left < right)
    {
        char temp = data[left];
        data[left] = data[right];
        data[right] = temp;
        left++;
        right--;
    }
}

//exemplo mais simples. porem complexidade O(n) tanto espaco quanto tempo
public static string ReverseWordsInAStringIII(string s)
{
    StringBuilder result = new StringBuilder();
    var words = s.Split(' ');

    foreach (var word in words) 
    {
        var reversedWord = new string(word.Reverse().ToArray());
        result.Append(reversedWord + " ");
    }

    return result.ToString().TrimEnd();
}
```

Versão em Python
``` Python
class Solution:  
    def reverseWords(self, s):  
        res = ''  
        l, r = 0, 0

        while r < len(s):  
            if s[r] != ' ':  
                r += 1  
            else:  
                res += s[l:r+1][::-1]  //concatena tudo e depois inverte
                r += 1  
                l = r

        res += ' '  
        res += s[l:r + 2][::-1]  
        return res[1:] //elimina o primeiro espaço colocado
```

Agora um exemplo do Two Sum, porém neste caso leva somente em consideração arrays ordenados, tem outras formas de fazer com ele desordenados.
```C#
public static int[] TwoSum(int[] arr, int target)
{
    if (arr is null)
        return [];

    int left = 0, right = arr.Length - 1;

    while (left < right) 
    {
        int sum = arr[left] + arr[right];
        if (sum == target)
            return [left + 1, right + 1];
        else if (sum > target)
            right--;
        else
            left++;            
    }

    return [];
}
```
