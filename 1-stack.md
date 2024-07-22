# Stack

## Introduction
A stack is a linear data structure that follows the Last In, First Out (LIFO) principle. It allows operations at one end only.

## Operations
- **Push:** Adds an element to the top of the stack.
- **Pop:** Removes the top element from the stack.
- **Peek:** Returns the top element without removing it.

## Performance Analysis
- Push: O(1)
- Pop: O(1)
- Peek: O(1)

## Example Problem
**Problem:** Implement a stack to reverse a string.

```csharp
public class Stack
{
    private List<char> elements = new List<char>();

    public void Push(char item)
    {
        elements.Add(item);
    }

    public char Pop()
    {
        if (elements.Count == 0) throw new InvalidOperationException("Stack is empty");
        char item = elements[elements.Count - 1];
        elements.RemoveAt(elements.Count - 1);
        return item;
    }

    public char Peek()
    {
        if (elements.Count == 0) throw new InvalidOperationException("Stack is empty");
        return elements[elements.Count - 1];
    }

    public bool IsEmpty()
    {
        return elements.Count == 0;
    }
}

// Usage
public static string ReverseString(string input)
{
    Stack stack = new Stack();
    foreach (char c in input)
    {
        stack.Push(c);
    }

    StringBuilder reversed = new StringBuilder();
    while (!stack.IsEmpty())
    {
        reversed.Append(stack.Pop());
    }

    return reversed.ToString();
}
