Стек — это коллекция, элементы которой получают по принципу «последний вошел, первый вышел» (Last-In-First-Out или LIFO). 
Это значит, что мы будем иметь доступ только к последнему добавленному элементу.

В отличие от списков, мы не можем получить доступ к произвольному элементу стека. 
Мы можем только добавлять или удалять элементы с помощью специальных методов. У стека нет также метода Contains, как у списков. 
Кроме того, у стека нет итератора.



Операция добавления элемента на стек называется *«push»*, удаления — *«pop»*. 
Последний добавленный элемент называется верхушкой стека, или *«top»*, и его можно посмотреть с помощью операции *«peek»*. 

    public class SimpleStack<T> {
    private ForwardLinked<T> linked = new ForwardLinked<T>();
    private int size = 0;

       public T pop() {
           size--;
           return linked.deleteFirst();

       }

       public void push(T value) {
           linked.addFirst(value);
           size++;
       }

       public boolean isEmpty() {
           return size == 0;
       }
    }