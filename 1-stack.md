# Stack

## Introduction
A stack is a linear data structure that follows the Last In First Out (LIFO) principle. Elements are added and removed from the top of the stack. This is similar to a stack of plates where you can only take the top plate off or add a plate to the top.

## Operations
- **Push:** Adds an element to the top of the stack.
- **Pop:** Removes the top element from the stack.
- **Peek:** Returns the top element without removing it.
- **IsEmpty**: Check if the stack is empty.

## Performance Analysis
- Push: O(1)
- Pop: O(1)
- Peek: O(1)
- IsEmpty: O(1)

## Example Problem
**Problem:** You are developing a browser history feature. Implement a stack to manage the browsing history. Each time a user visits a new page, push the URL onto the stack. When the user clicks the back button, pop the top URL from the stack.

```csharp
using System;
using System.Collections.Generic;
class BrowserHistory
{
    private Stack<string> history = new Stack<string>();

    public void Visit(string url)
    {
        history.Push(url);
        Console.WriteLine($"Visited: {url}");
    }

    public void Back()
    {
        if (history.Count > 0)
        {
            string url = history.Pop();
            Console.WriteLine($"Back to: {url}");
        }
        else
        {
            Console.WriteLine("No history available.");
        }
    }

    public void ShowHistory()
    {
        Console.WriteLine("Browsing History:");
        foreach (var url in history)
        {
            Console.WriteLine(url);
        }
    }
}

class Program
{
    static void Main()
    {
        BrowserHistory browserHistory = new BrowserHistory();
        browserHistory.Visit("http://example.com");
        browserHistory.Visit("http://example.com/about");
        browserHistory.Visit("http://example.com/contact");

        browserHistory.ShowHistory();
        browserHistory.Back();
        browserHistory.ShowHistory();
    }
}