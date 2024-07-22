
#### 3-topic.md (Tree)
```markdown
# Tree

## Introduction
A tree is a hierarchical data structure consisting of nodes, where each node has zero or more child nodes. The top node is called the root.

## Types of Trees
- Binary Tree
- Binary Search Tree (BST)
- AVL Tree

## Operations
- **Insertion:** Add a new node.
- **Deletion:** Remove a node.
- **Traversal:** In-order, pre-order, post-order

## Performance Analysis
- Insertion: O(log n) for balanced trees
- Deletion: O(log n) for balanced trees
- Traversal: O(n)

## Example Problem
**Problem:** Implement a binary search tree (BST) and perform in-order traversal.

```csharp
public class TreeNode
{
    public int Data;
    public TreeNode Left;
    public TreeNode Right;

    public TreeNode(int data)
    {
        Data = data;
        Left = null;
        Right = null;
    }
}

public class BinarySearchTree
{
    private TreeNode root;

    public void Insert(int data)
    {
        root = InsertRec(root, data);
    }

    private TreeNode InsertRec(TreeNode root, int data)
    {
        if (root == null)
        {
            root = new TreeNode(data);
            return root;
        }

        if (data < root.Data)
        {
            root.Left = InsertRec(root.Left, data);
        }
        else if (data > root.Data)
        {
            root.Right = InsertRec(root.Right, data);
        }

        return root;
    }

    public void InOrderTraversal()
    {
        InOrderRec(root);
    }

    private void InOrderRec(TreeNode root)
    {
        if (root != null)
        {
            InOrderRec(root.Left);
            Console.WriteLine(root.Data);
            InOrderRec(root.Right);
        }
    }
}

// Usage
BinarySearchTree bst = new BinarySearchTree();
bst.Insert(50);
bst.Insert(30);
bst.Insert(20);
bst.Insert(40);
bst.Insert(70);
bst.Insert(60);
bst.Insert(80);
bst.InOrderTraversal(); // Output: 20, 30, 40, 50, 60, 70, 80
