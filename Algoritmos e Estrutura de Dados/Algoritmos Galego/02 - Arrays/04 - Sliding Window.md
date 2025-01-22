Um dos tipos de questões mais populares que tem.
Conseguimos identificar se é possível utilizar esta técnica quando a solução do problema é um  sub-array ou tamanho de um sub-array, ou sub-string, ou tamanho de sub-string que preenche uma certa condição.
Temos uma "receita de bolo" quando identificarmos este tipo de problema, que seria:

	max
	While
		R++
		 While
			 L++
 Basicamente essa janela esta expandindo e depois contraindo.
 E nestes Whiles você fará a checagem, contabilidade, depende do que o problema requer.
 Precisaremos de algumas uma estrutura de dados para contabilizar o quanto cada caractere já se repetiu. Uma que faz muito sentido é o HashMap.
 
O exemplo que faremos será de encontrar o array onde um elemento de uma string não pode repetir mais de uma vez. https://leetcode.com/problems/maximum-length-substring-with-two-occurrences/
```C#
    public static int MaximumLengthSubstring(string s)
    {
        var str = s.ToArray();
        int left = 0, right = 0, _max = 1;    
        Dictionary<char, int> counter = new Dictionary<char, int>();
        counter.Add(s[0], 1);

        while (right < str.Length - 1)
        {
            right++;
            if (counter.ContainsKey(str[right]))
                counter[str[right]]++;
            else
                counter[s[right]] = 1;

            while (counter[str[right]] == 3)
            {
                counter[str[left]]--;
                left++;
            }

            _max = Math.Max(_max, right - left + 1);
        }

        return _max;
    }
```

Exemplo de um array e fazendo a maior soma de 5 em cinco
```C#
    public static int BiggestSumInArray(int[] arr)
    {
        int l = 0, r = 4, _sum = 0;

        for (int i = 0; i <= r; i++)
            _sum += arr[i];

        int _max = _sum;

        while (r < arr.Length - 1)
        {               
            r++;
            _sum = (_sum + arr[r]) - arr[l];
            l++;

            _max = Math.Max(_max, _sum);
        }

        return _max;
    }
```
