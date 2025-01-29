Temos algumas maneiras de fazer isso, uma seria percorrer a lista e usar um contador para ver quantos elementos tem na lista.
Mas aqui adotaremos o uso de uma variável auxiliar que percorre o dobro de elementos que o head, e quando essa variável chegar ao fim da lista o head vai se encontrar no meio da lista.
```C#
 public static ListNode MiddleNode(ListNode head)
 {
     var Ahead = head;

     while (Ahead != null && Ahead.next != null) 
     {
         Ahead = Ahead.next.next;
         head = head.next;
     }

     return head;
```