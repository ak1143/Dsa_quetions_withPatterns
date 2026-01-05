-

## 🌳 Binary Tree – Basic to Advanced Notes


### 1. What is a Binary Tree?

A tree data structure where **each node has at most two children**:

* Left child
* Right child

---

### 2. Types of Binary Trees

* **Full Binary Tree**: Each node has 0 or 2 children
* **Complete Binary Tree**: All levels filled except possibly last (left-filled)
* **Perfect Binary Tree**: All internal nodes have 2 children & all leaves at same level
* **Skewed Binary Tree**: Every node has only one child

---

### 3. Basic Terminology

* **Root**: Top node
* **Leaf**: Node with no children
* **Height**: Longest path from node to leaf
* **Depth**: Distance from root
* **Level**: Depth + 1

---

### 4. Tree Traversals (VERY IMPORTANT)

**DFS Traversals**

* **Preorder** → Root → Left → Right
* **Inorder** → Left → Root → Right
* **Postorder** → Left → Right → Root

**BFS Traversal**

* **Level Order** (uses Queue)

---

### 5. Recursive Tree Template (Interview Must)

```java
void dfs(TreeNode root) {
    if (root == null) return;
    dfs(root.left);
    dfs(root.right);
}
```

---

### 6. Height & Depth Pattern

* Height is usually calculated **bottom-up**
* Used in:

  * Diameter of tree
  * Balanced tree check

---

### 7. Common Binary Tree Problems

* Maximum / Minimum depth
* Diameter of Binary Tree
* Check if tree is balanced
* Invert Binary Tree

---

### 8. Path-Based Problems

* Root-to-leaf path sum
* Maximum path sum
* Count paths with given sum

---

### 9. Binary Tree vs Binary Search Tree

* **Binary Tree** → No ordering rule
* **BST** → Left < Root < Right

(Inorder traversal of BST gives **sorted order**)

---

### 10. Iterative Traversals (Stack / Queue)

* Stack → DFS
* Queue → BFS

Used when recursion is not allowed.

---

### 11. Advanced Patterns (Know Names Only)

* Diameter Pattern
* Lowest Common Ancestor (LCA)
* Boundary Traversal
* Vertical / Zigzag Traversal

---

### 12. Time Complexity (General Rule)

* **Traversal** → `O(n)`
* **Space** → `O(h)` (recursion stack)

---

# 🌳 Binary Tree – All Implementations (Java)


## 1️⃣ Tree Node Definition (Base)

```java
class TreeNode {
    int val;
    TreeNode left, right;

    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}
```

---

## 2️⃣ Tree Creation

### a) Manual Creation

```java
TreeNode root = new TreeNode(1);
root.left = new TreeNode(2);
root.right = new TreeNode(3);
```

### b) From Level Order (Using Queue)

```java
Queue<TreeNode> q = new LinkedList<>();
q.offer(root);
```

---

## 3️⃣ Tree Traversals (MOST IMPORTANT)

### ✅ Depth First Traversals (DFS)

#### 1. Preorder (Root → Left → Right)

```java
void preorder(TreeNode root) {
    if (root == null) return;
    System.out.print(root.val + " ");
    preorder(root.left);
    preorder(root.right);
}
```

#### 2. Inorder (Left → Root → Right)

```java
void inorder(TreeNode root) {
    if (root == null) return;
    inorder(root.left);
    System.out.print(root.val + " ");
    inorder(root.right);
}
```

#### 3. Postorder (Left → Right → Root)

```java
void postorder(TreeNode root) {
    if (root == null) return;
    postorder(root.left);
    postorder(root.right);
    System.out.print(root.val + " ");
}
```

---

### ✅ Breadth First Traversal (BFS)

#### 4. Level Order

```java
void levelOrder(TreeNode root) {
    if (root == null) return;

    Queue<TreeNode> q = new LinkedList<>();
    q.offer(root);

    while (!q.isEmpty()) {
        TreeNode node = q.poll();
        System.out.print(node.val + " ");

        if (node.left != null) q.offer(node.left);
        if (node.right != null) q.offer(node.right);
    }
}
```

---

## 4️⃣ Height / Depth of Tree

```java
int height(TreeNode root) {
    if (root == null) return 0;
    return 1 + Math.max(height(root.left), height(root.right));
}
```

---

## 5️⃣ Count Nodes

```java
int countNodes(TreeNode root) {
    if (root == null) return 0;
    return 1 + countNodes(root.left) + countNodes(root.right);
}
```

---

## 6️⃣ Count Leaf Nodes

```java
int countLeaves(TreeNode root) {
    if (root == null) return 0;
    if (root.left == null && root.right == null) return 1;
    return countLeaves(root.left) + countLeaves(root.right);
}
```

---

## 7️⃣ Search an Element

```java
boolean search(TreeNode root, int key) {
    if (root == null) return false;
    if (root.val == key) return true;
    return search(root.left, key) || search(root.right, key);
}
```

---

## 8️⃣ Maximum & Minimum Value

```java
int maxValue(TreeNode root) {
    if (root == null) return Integer.MIN_VALUE;
    return Math.max(root.val,
           Math.max(maxValue(root.left), maxValue(root.right)));
}
```

---

## 9️⃣ Mirror / Invert Binary Tree

```java
TreeNode invert(TreeNode root) {
    if (root == null) return null;

    TreeNode left = invert(root.left);
    TreeNode right = invert(root.right);

    root.left = right;
    root.right = left;

    return root;
}
```

---

## 🔟 Check Identical Trees

```java
boolean isSame(TreeNode a, TreeNode b) {
    if (a == null && b == null) return true;
    if (a == null || b == null) return false;
    return a.val == b.val &&
           isSame(a.left, b.left) &&
           isSame(a.right, b.right);
}
```

---

## 1️⃣1️⃣ Check Symmetric Tree

```java
boolean isSymmetric(TreeNode root) {
    return isMirror(root.left, root.right);
}

boolean isMirror(TreeNode a, TreeNode b) {
    if (a == null && b == null) return true;
    if (a == null || b == null) return false;
    return a.val == b.val &&
           isMirror(a.left, b.right) &&
           isMirror(a.right, b.left);
}
```

---

## 1️⃣2️⃣ Diameter of Binary Tree

```java
int diameter = 0;

int diameterOfBinaryTree(TreeNode root) {
    height(root);
    return diameter;
}

int height(TreeNode root) {
    if (root == null) return 0;
    int lh = height(root.left);
    int rh = height(root.right);
    diameter = Math.max(diameter, lh + rh);
    return 1 + Math.max(lh, rh);
}
```

---

## 1️⃣3️⃣ Right Side View (Your Question Type)

```java
List<Integer> rightSideView(TreeNode root) {
    List<Integer> res = new ArrayList<>();
    if (root == null) return res;

    Queue<TreeNode> q = new LinkedList<>();
    q.offer(root);

    while (!q.isEmpty()) {
        int size = q.size();
        TreeNode node = null;

        while (size-- > 0) {
            node = q.poll();
            if (node.left != null) q.offer(node.left);
            if (node.right != null) q.offer(node.right);
        }
        res.add(node.val);
    }
    return res;
}
```

---

## 1️⃣4️⃣ Lowest Common Ancestor (Binary Tree)

```java
TreeNode LCA(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null || root == p || root == q) return root;

    TreeNode left = LCA(root.left, p, q);
    TreeNode right = LCA(root.right, p, q);

    if (left != null && right != null) return root;
    return left != null ? left : right;
}
```

---

