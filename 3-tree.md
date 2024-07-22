
### 3-tree.md

```markdown
# Tree

A tree is a hierarchical data structure consisting of nodes, where each node has zero or more child nodes. The topmost node is called the root, and the nodes without children are called leaves.

## Types of Trees
- **Binary Tree**: Each node has at most two children.
- **Binary Search Tree**: A binary tree where the left child contains values less than the parent node, and the right child contains values greater than the parent node.

## Operations
- **Insert**: Add a node to the tree.
- **Delete**: Remove a node from the tree.
- **Search**: Find a node in the tree.
- **Traverse**: Visit all nodes in a specific order (Inorder, Preorder, Postorder).

## Performance
- Insert: O(log n) on average.
- Delete: O(log n) on average.
- Search: O(log n) on average.

## Example Problem
### Problem
Implement a binary search tree to manage a contact list. Each contact is stored in a node, and you can add new contacts, remove contacts, and search for contacts.

### Solution
```csharp
using System;

class TreeNode
{
    public string Name;
    public string PhoneNumber;
    public TreeNode Left;
    public TreeNode Right;

    public TreeNode(string name, string phoneNumber)
    {
        Name = name;
        PhoneNumber = phoneNumber;
        Left = null;
        Right = null;
    }
}

class ContactList
{
    private TreeNode root;

    public void AddContact(string name, string phoneNumber)
    {
        root = AddContact(root, name, phoneNumber);
    }

    private TreeNode AddContact(TreeNode node, string name, string phoneNumber)
    {
        if (node == null)
        {
            return new TreeNode(name, phoneNumber);
        }

        if (string.Compare(name, node.Name) < 0)
        {
            node.Left = AddContact(node.Left, name, phoneNumber);
        }
        else
        {
            node.Right = AddContact(node.Right, name, phoneNumber);
        }

        return node;
    }

    public bool SearchContact(string name)
    {
        return SearchContact(root, name);
    }

    private bool SearchContact(TreeNode node, string name)
    {
        if (node == null)
        {
            return false;
        }

        if (node.Name == name)
        {
            Console.WriteLine($"Found: {node.Name} - {node.PhoneNumber}");
            return true;
        }

        if (string.Compare(name, node.Name) < 0)
        {
            return SearchContact(node.Left, name);
        }
        else
        {
            return SearchContact(node.Right, name);
        }
    }

    public void ShowContacts()
    {
        InOrderTraversal(root);
    }

    private void InOrderTraversal(TreeNode node)
    {
        if (node != null)
        {
            InOrderTraversal(node.Left);
            Console.WriteLine($"{node.Name} - {node.PhoneNumber}");
            InOrderTraversal(node.Right);
        }
    }
}

class Program
{
    static void Main()
    {
        ContactList contactList = new ContactList();
        contactList.AddContact("Alice", "123-456-7890");
        contactList.AddContact("Bob", "987-654-3210");
        contactList.AddContact("Charlie", "555-555-5555");

        contactList.ShowContacts();
        contactList.SearchContact("Bob");
    }
}
