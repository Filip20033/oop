package myqueueadt;

/**
 *
 * @author filip
 */
import java.util.LinkedList;
import java.util.Queue;

import java.util.LinkedList;
import java.util.Queue;

/**
 * Queue implementation in Java for the OS queue ADT.
 * @author tenhe
 */

// Interface for queue operations
interface MyQueueADT {
    void enqueue(String item);
    String dequeue();
    String front();
    int size();
    boolean isEmpty();
}

// Queue implementation
public class MyQueue implements MyQueueADT {
    private Queue<String> queue;

    public MyQueue() {
        queue = new LinkedList<>();
    }

    @Override
    public void enqueue(String item) {
        queue.add(item);
    }

    @Override
    public String dequeue() {
        if (queue.isEmpty()) {
            System.out.println("Queue is empty! Cannot dequeue.");
            return null;
        }
        return queue.poll();
    }

    @Override
    public String front() {
        if (queue.isEmpty()) {
            System.out.println("Queue is empty! No front element.");
            return null;
        }
        return queue.peek();
    }

    @Override
    public int size() {
        return queue.size();
    }

    @Override
    public boolean isEmpty() {
        return queue.isEmpty();
    }

    public static void main(String[] args) {
        MyQueueADT mq = new MyQueue();

        // Add three string items
        mq.enqueue("Task 1");
        mq.enqueue("Task 2");
        mq.enqueue("Task 3");

        // Check queue size
        System.out.println("Queue size: " + mq.size());

        // Add seven more items
        mq.enqueue("Task 4");
        mq.enqueue("Task 5");
        mq.enqueue("Task 6");
        mq.enqueue("Task 7");
        mq.enqueue("Task 8");
        mq.enqueue("Task 9");
        mq.enqueue("Task 10");

        // Check queue size after adding more elements
        System.out.println("Queue size after adding more elements: " + mq.size());

        // Print the element at the front
        System.out.println("Front element: " + mq.front());

        // Remove and print each item, checking queue size after each removal
        System.out.println("Removing all items...");
        while (!mq.isEmpty()) {
            System.out.println("Dequeued: " + mq.dequeue() + " | New size: " + mq.size());
        }

        // Try removing from an empty queue
        System.out.println("Trying to dequeue from an empty queue:");
        mq.dequeue();
    }
}
