Podemos usar uma lista auxiliar para salvar os elementos, e uma variável temporária para pegar o próximo elemento da lista original, e assim apontar para o anterior.
```C#
 public static ListNode ReverseList(ListNode head)
 {
     ListNode newList = null;

     while (head != null) 
     {
         var nextNode = head.next;
         head.next = newList;
         newList = head;
         head = nextNode;
     }

     return newList;
 }
```