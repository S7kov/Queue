public class MyQueue<T> {
    private static class Node<T> {
        T data;
        Node<T> next;
        
        Node(T data) {
            this.data = data;
            this.next = null;
        }
    }
    
    private Node<T> front;
    private Node<T> rear;
    private int size;
    
    public MyQueue() {
        front = null;
        rear = null;
        size = 0;
    }
    
    // Добавление элемента в очередь
    public void enqueue(T item) {
        Node<T> newNode = new Node<>(item);
        if (rear == null) {
            front = newNode;
            rear = newNode;
        } else {
            rear.next = newNode;
            rear = newNode;
        }
        size++;
    }
    
    // Удаление элемента из очереди
    public T dequeue() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue is empty");
        }
        T item = front.data;
        front = front.next;
        if (front == null) {
            rear = null;
        }
        size--;
        return item;
    }
    
    // Получение первого элемента без удаления
    public T peek() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue is empty");
        }
        return front.data;
    }
    
    // Проверка на пустоту
    public boolean isEmpty() {
        return front == null;
    }
    
    // Размер очереди
    public int size() {
        return size;
    }
    
    // Очистка очереди
    public void clear() {
        front = null;
        rear = null;
        size = 0;
    }
}
