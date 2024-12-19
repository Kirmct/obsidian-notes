## Funções Hash
Como exemplo imagine que estamos em um mercado, somos atendentes, um cliente chega e pergunta qual valor da maçã, qual seria uma boa maneira de armazenar essa informação?
Seria ideal que a busca fosse feita o mais rápido possível, se for por meio de listas teremos um tempo de busca de O(n), se for array sera O(1), porém arrays somente guardam um tipo de imformação.
A solução seria a Tabela Hash, uma estrutura de dados que consiste em guardar uma chave e um valor, esta chave funciona como o índice de um array, ou seja, sua busca tem tempo constante e bem rápido de O(1)!
Mapeia strings e números, deve se consistente. Mapeia diferentes dados para diferentes números.
As funções hash são algoritmos que buscam fazer isso para nós, elas trabalhar com essas funções e array para criar essa estrutura de dados, maioria das linguagens já vem com implementação da tabela hash, então não nos preocupamos como essa função hash irá trabalhar por baixo dos panos.

	São extremamente recomendadas quando você deseja mapear um item com relação a outro, como um produto e um preço, um nome e um número, etc.
	A pesquisa por chaves é extremamente eficiente, no caso médio sendo O(1)

## Evitando entradas duplicadas
Elas são boas quando não queremos que o mesmo item seja adicionado duas vezes, ou mesmo para termos maior controle sobre isso.
Podemos imaginar uma votação, onde cada pessoa só tem direito a 1 voto, se a mesma pessoa tentar votar novamente a consulta ao dado será muito mais rápida, e assim podemos evitar isso.

## Tabela Hash como Cache
O cache funciona como: os websites lembram dos dados em vez de recalculá-los a cada solicitação. Fazendo o acesso ser muito mais rápido, e não sobrecarregando o servidor.

## Colisões
Pode haver problemas ao armazenar dois itens no mesmo endereço de memória, isso seria um problema. Podemos burlar salvando uma lista linkada neste item, porém sua busca seria O(1) na tabela, e depois O(n) dentro desta lista, o que acaba não sendo eficaz.

## Desempenho
Caso médio:
- Procura: O(1)
- Inserção: O(1)
- Deleção: O(1)

Pior caso:
- Procura: O(n)
- Inserção: O(n)
- Deleção: O(n)

É de extrema importância não trabalhar no pior caso, devemos evitar colisões, e para isso podemos:
- Ter um baixo fator de carga
- Uma boa função hash

## Fator de Carga
Tabelas hash utilizam arrays para armazenamento, você deve contar o número de espaços usasdos no array.
O fator de carga mede quantos espaços continuam vazios na sua tabela hash. Exemplo, um array de 5 posições e duas delas estão preenchidas, o fator de carga deste seria 3/5.
Fator chegar em 1 é caso extremo, e teriamos que redimensionar tudo, o que já vimos sendo algo bem ruim usando arrays.
Devemos tentar manter o fator de carga de no mínimo 0.7
