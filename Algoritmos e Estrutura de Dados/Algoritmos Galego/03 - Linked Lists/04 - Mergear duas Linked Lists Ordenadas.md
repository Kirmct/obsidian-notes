Aqui vamos usar de uma lista auxiliar para ir salvando os elementos em ordem de ordenação, também usaremos um nodo current para percorrer as duas outras listas.
```C#
 public static ListNode MergeTwoLists(ListNode list1, ListNode list2)
 {
     var result = new ListNode(-1);
     var current = result;

     while(list1 is not null && list2 is not null)
     {
         if(list1.val <= list2.val)
         {
             current.next = list1;
             list1 = list1.next;
         }
         else
         {
             current.next = list2;
             list2 = list2.next;
         }
         current = current.next;
     }

     current.next = list1 ?? list2;

     return result.next;
 }
```