
#### 2-topic.md (Linked List)
```markdown
# Linked List

## Introduction
A linked list is a linear data structure where each element is a separate object, called a node, and contains a reference to the next node in the sequence.

## Types of Linked Lists
- Singly Linked List
- Doubly Linked List
- Circular Linked List

## Operations
- **Insertion:** Add a new node.
- **Deletion:** Remove a node.
- **Traversal:** Access each node sequentially.

## Performance Analysis
- Insertion: O(1)
- Deletion: O(1)
- Traversal: O(n)

## Example Problem
**Problem:** Implement a singly linked list to store integers.

```csharp
public class Node
{
    public int Data;
    public Node Next;

    public Node(int data)
    {
        Data = data;
        Next = null;
    }
}

public class LinkedList
{
    private Node head;

    public void Insert(int data)
    {
        Node newNode = new Node(data);
        if (head == null)
        {
            head = newNode;
        }
        else
        {
            Node current = head;
            while (current.Next != null)
            {
                current = current.Next;
            }
            current.Next = newNode;
        }
    }

    public void Delete(int data)
    {
        if (head == null) return;

        if (head.Data == data)
        {
            head = head.Next;
            return;
        }

        Node current = head;
        while (current.Next != null && current.Next.Data != data)
        {
            current = current.Next;
        }

        if (current.Next != null)
        {
            current.Next = current.Next.Next;
        }
    }

    public void PrintList()
    {
        Node current = head;
        while (current != null)
        {
            Console.WriteLine(current.Data);
            current = current.Next;
        }
    }
}

// Usage
LinkedList list = new LinkedList();
list.Insert(1);
list.Insert(2);
list.Insert(3);
list.PrintList(); // Output: 1, 2, 3
