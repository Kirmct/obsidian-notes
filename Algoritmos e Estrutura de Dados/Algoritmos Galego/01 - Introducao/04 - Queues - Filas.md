Segue a regra de FIFO (First In First Out).
Usada para fazer buffering, streaming de dados.
Um padrão bem usado é feito por linked lists.
Aponta uma referência para o início e um para o fim (Head and Tail).
Inserção e remoção (primeiro e último) -> O(1)

## Dequeue
Não necessariamente FIFO, podemos inserir e remover de ambos lados.
Usada com doubly-linked lists