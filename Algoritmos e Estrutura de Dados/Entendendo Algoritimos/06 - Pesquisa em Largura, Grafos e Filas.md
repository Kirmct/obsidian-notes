## Pesquisa em largura
Permite encontrar o menor caminho entre dois objetos, e isto pode significar muitas coisas, como:
- Um algoritmo de IA que calcula menor número de movimentos para finalizar o jogo de damas;
- Um corretor ortográfico (menor número de edições para corrigir uma palavra);
- Encontrar algo mais próximo de você, como um médico.

## Grafos
Digamos que está em Manaus, e quer saber qual caminho mais rápido para chegar a Ponte.
Usamos o algoritmo de pesquisa em largura para fazer isso, ele descobre o caminho mais curto até a ponte, o que demandaria menos etapas.

### O que é um grafo
É um conjunto de conexões.
Cada grafo é constituído de vértices e arestas.
Um vértice pode estar conectados a diversos outros vértices, neste caso são chamados de vértices vizinhos.
Grafos são uma maneira de modelar como eventos diferentes estão conectados entre sim.

## Pesquisa em Largura na Prática
Este algoritmo ajuda e responder dois tipos de pergunta:
- Existe algum caminho do vértice A até o vértice B?
- Qual o caminho mínimo do vértice A até o B?

Caso você esteja atrás de algum vendedor de uvas, você primeiro pesquisa entre seus amigos se algum vende, se nenhum vender você pesquisará entre os amigos deles também. Pesquisa em toda sua rede para tentar encontrar.

### Encontrando o Caminho Mínimo
Você sempre prefere uma conexão de primeiro grau em vez de conexões de segundo, ou terceiro, etc.
Você sempre pesquisará primeiro nas de primeiro, se não achar aí sim que irá para as próximas.
Assim, a pesquisa em largura faz com que a pesquisa irradie a partir do ponto inicial.
Para isto é necessário pesquisar as pessoas na ordem em que elas foram adicionadas, e para isso existe uma estrutura de dados específica: a fila;

## Fila
Funciona exatamente como a fila na vida real.
Não é possível inserir elementos aleatórios em uma fila. Só podemos fazer duas operações, inserir no final, ou remover do início (FIFO - First in first out).

## Implementando o Grafo
Como fazer a conexão dos vértice com um vizinho? é possível fazer isso usando uma [[05 - Tabela Hash]]
Ela lhe permite mapear uma chave e um valor. No caso devemos mapear um vértice para todos os seus vizinhos.

```C#
using System;
using System.Collections.Generic;
using System.Linq;

namespace ConsoleApplication
{
    public class Program
    {
        private static Dictionary<string, string[]> _graph = new Dictionary<string, string[]>();

        public static void Main(string[] args)
        {
            _graph.Add("you", new[] { "alice", "bob", "claire" });
            _graph.Add("bob", new[] { "anuj", "peggy" });
            _graph.Add("alice", new[] { "peggy" });
            _graph.Add("claire", new[] { "thom", "jonny" });
            _graph.Add("anuj", Array.Empty<string>());
            _graph.Add("peggy", Array.Empty<string>());
            _graph.Add("thom", Array.Empty<string>());
            _graph.Add("jonny", Array.Empty<string>());
            Search("you");
        }

        private static bool Search(string name)
        {
            var searchQueue = new Queue<string>(_graph[name]);
            var searched = new List<string>();
            while (searchQueue.Any())
            {
                var person = searchQueue.Dequeue();
                if (!searched.Contains(person))
                {
                    if (PersonIsSeller(person))
                    {
                        Console.WriteLine($"{person} is a mango seller");
                        return true;
                    }
                    else
                    {
                        searchQueue = new Queue<string>(searchQueue.Concat(_graph[person]));
                        searched.Add(person);
                    }
                }
            }
            return false;
        }

        private static bool PersonIsSeller(string name)
        {
            return name.EndsWith("m");
        }
    }
}
```
Notemos que fizemos a verificação para caso uma pessoa já tenha sido vista anteriormente, isto para que não gere problemas com loops infinitos e para poupar processamento. Criamos uma lista de pessoas  verificadas para isso.

