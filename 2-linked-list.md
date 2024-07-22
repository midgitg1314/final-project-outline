
### 2-linked_list.md

```markdown
# Linked List

A linked list is a linear data structure where elements are stored in nodes, and each node points to the next node. This structure allows for efficient insertions and deletions.

## Types of Linked Lists
- **Singly Linked List**: Each node points to the next node.
- **Doubly Linked List**: Each node points to both the next and the previous node.
- **Circular Linked List**: The last node points back to the first node.

## Operations
- **Insert**: Add an element at a specific position.
- **Delete**: Remove an element from a specific position.
- **Search**: Find an element in the list.

## Performance
- Insert: O(1) for inserting at the beginning.
- Delete: O(1) for deleting from the beginning.
- Search: O(n)

## Example Problem
### Problem
Implement a singly linked list to manage a to-do list. Each task is stored in a node, and you can add new tasks or remove completed tasks.

### Solution
```csharp
using System;

class Node
{
    public string Task;
    public Node Next;

    public Node(string task)
    {
        Task = task;
        Next = null;
    }
}

class ToDoList
{
    private Node head;

    public void AddTask(string task)
    {
        Node newNode = new Node(task);
        newNode.Next = head;
        head = newNode;
    }

    public void RemoveTask()
    {
        if (head != null)
        {
            head = head.Next;
        }
    }

    public void ShowTasks()
    {
        Node current = head;
        while (current != null)
        {
            Console.WriteLine(current.Task);
            current = current.Next;
        }
    }
}

class Program
{
    static void Main()
    {
        ToDoList toDoList = new ToDoList();
        toDoList.AddTask("Buy groceries");
        toDoList.AddTask("Clean the house");
        toDoList.AddTask("Pay bills");

        toDoList.ShowTasks();
        toDoList.RemoveTask();
        toDoList.ShowTasks();
    }
}
