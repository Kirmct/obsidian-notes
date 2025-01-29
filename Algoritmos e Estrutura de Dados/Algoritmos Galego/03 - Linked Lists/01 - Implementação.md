## Node
Cada nó que aponta para o próximo nó, criando assim a lista.
Temos um ponteiro que aponta para Head, o primeiro nó da lista.
Pode apontar para o prox e anterior, sendo assim uma doubly linked list.
Numa doubly temos um ponteiro que aponta para Tail, o último elemento da lista.

```C#
public class Node<T>
{
    public T Data { get; set; }
    public Node<T>? Next { get; set; }
    public Node<T>? Prev { get; set; }

    public Node(T data)
    {
        Data = data;
        Next = null;
        Prev = null;
    }
}

public class DoublyLinkList<T>
{
    public Node<T>? Head { get; set; }
    public Node<T>? Tail { get; set; }

    public DoublyLinkList()
    {
        Head = null;
        Tail = null;
    }

    public void AddToFront(T data)
    {
        var newNode = new Node<T>(data);
        newNode.Next = Head;

        if (Head is not null)
            Head.Prev = newNode;
        else
            Tail = newNode;

        Head = newNode;
    }

    public void AddToEnd(T data)
    {
        var newNode = new Node<T>(data);
        newNode.Prev = Tail;

        if (Tail is not null)
            Tail.Next = newNode;
        else
            Head = newNode;

        Tail = newNode;
    }

    public T RemoveToFront()
    {
        if (Head is null)
            return default!;

        var removedData = Head.Data;

        Head = Head.Next;

        if (Head is not null)
            Head.Prev = null;
        else
            Tail = null;

        return removedData;
    }

    public T RemoveToEnd()
    {
        if (Tail is null)
            return default!;

        var removedData = Tail.Data;

        Tail = Tail.Prev;

        if (Tail is not null)
            Tail.Next = null;
        else
            Head = null;

        return removedData;
    }
}
```