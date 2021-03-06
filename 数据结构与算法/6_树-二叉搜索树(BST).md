# ð¤ðæ  - äºåæç´¢æ (BST)

äºåæ ä¸­æåºæ¬çäºåæ¥æ¾æ ï¼Binary Search Treeï¼ï¼ï¼åï¼äºåæç´¢æ ï¼äºåæåºæ ï¼å®æèæ¯ä¸æ£µç©ºæ ï¼æèæ¯å·æä¸åæ§è´¨çäºåæ ï¼ è¥å®çå·¦å­æ ä¸ç©ºï¼åå·¦å­æ ä¸ææç»ç¹çå¼åå°äºå®çæ ¹ç»ç¹çå¼ï¼ è¥å®çå³å­æ ä¸ç©ºï¼åå³å­æ ä¸ææç»ç¹çå¼åå¤§äºå®çæ ¹ç»ç¹çå¼ï¼ å®çå·¦ãå³å­æ ä¹åå«ä¸ºäºåæåºæ ã

## BSTçå®ä¹

å¨äºåæ¥æ¾æ ä¸­:

- è¥ä»»æèç¹çå·¦å­æ ä¸ç©ºï¼åå·¦å­æ ä¸ææç»ç¹çå¼åå°äºå®çæ ¹ç»ç¹çå¼ï¼
- ä»»æèç¹çå³å­æ ä¸ç©ºï¼åå³å­æ ä¸ææç»ç¹çå¼åå¤§äºå®çæ ¹ç»ç¹çå¼ï¼
- ä»»æèç¹çå·¦ãå³å­æ ä¹åå«ä¸ºäºåæ¥æ¾æ ã
- æ²¡æé®å¼ç¸ç­çèç¹ã

![alg-tree-binary-search-1](Images/alg-tree-binary-search-1.svg)

![alg-tree-binary-search-0](Images/alg-tree-binary-search-0.png)

## BSTçå®ç°

### èç¹

BSTreeæ¯äºåæ ï¼å®ä¿æ¤äºäºåæ çæ ¹èç¹mRootï¼mRootæ¯BSTNodeç±»åï¼èBSTNodeæ¯äºåæ¥æ¾æ çèç¹ï¼å®æ¯BSTreeçåé¨ç±»ãBSTNodeåå«äºåæ¥æ¾æ çå ä¸ªåºæ¬ä¿¡æ¯:

- key -- å®æ¯å³é®å­ï¼æ¯ç¨æ¥å¯¹äºåæ¥æ¾æ çèç¹è¿è¡æåºçã
- left -- å®æåå½åèç¹çå·¦å­©å­ã
- right -- å®æåå½åèç¹çå³å­©å­ã
- parent -- å®æåå½åèç¹çç¶ç»ç¹ã

```java
public class BSTree<T extends Comparable<T>> {

    private BSTNode<T> mRoot;    // æ ¹ç»ç¹

    public class BSTNode<T extends Comparable<T>> {
        T key;                // å³é®å­(é®å¼)
        BSTNode<T> left;      // å·¦å­©å­
        BSTNode<T> right;     // å³å­©å­
        BSTNode<T> parent;    // ç¶ç»ç¹

        public BSTNode(T key, BSTNode<T> parent, BSTNode<T> left, BSTNode<T> right) {
            this.key = key;
            this.parent = parent;
            this.left = left;
            this.right = right;
        }
    }

        ......
}
```

### éå

è¿éè®²è§£ååºéåãä¸­åºéåãååºéå3ç§æ¹å¼ã

#### ååºéå

è¥äºåæ éç©ºï¼åæ§è¡ä»¥ä¸æä½:

- è®¿é®æ ¹ç»ç¹ï¼
- ååºéåå·¦å­æ ï¼
- ååºéåå³å­æ ã

```java
private void preOrder(BSTNode<T> tree) {
    if(tree != null) {
        System.out.print(tree.key+" ");
        preOrder(tree.left);
        preOrder(tree.right);
    }
}

public void preOrder() {
    preOrder(mRoot);
}
```

#### ä¸­åºéå

è¥äºåæ éç©ºï¼åæ§è¡ä»¥ä¸æä½:

- ä¸­åºéåå·¦å­æ ï¼
- è®¿é®æ ¹ç»ç¹ï¼
- ä¸­åºéåå³å­æ ã

```java
private void inOrder(BSTNode<T> tree) {
    if(tree != null) {
        inOrder(tree.left);
        System.out.print(tree.key+" ");
        inOrder(tree.right);
    }
}

public void inOrder() {
    inOrder(mRoot);
}
```

#### ååºéå

è¥äºåæ éç©ºï¼åæ§è¡ä»¥ä¸æä½:

- ååºéåå·¦å­æ ï¼
- ååºéåå³å­æ ï¼
- è®¿é®æ ¹ç»ç¹ã

```java
private void postOrder(BSTNode<T> tree) {
    if(tree != null)
    {
        postOrder(tree.left);
        postOrder(tree.right);
        System.out.print(tree.key+" ");
    }
}

public void postOrder() {
    postOrder(mRoot);
}
```

ççä¸é¢è¿é¢æ çåç§éåæ¹å¼:

![alg-tree-binary-search-1 (1)](Images/alg-tree-binary-search-1%20(1).svg)

å¯¹äºä¸é¢çäºåæ èè¨ï¼

- ååºéåç»æ:  8 3 1 6 4 7 10 14 13
- ä¸­åºéåç»æ:  1 3 4 6 7 8 10 13 14
- ååºéåç»æ:  1 4 7 6 3 13 14 10 8

### æ¥æ¾

- éå½çæ¬çä»£ç 

```java
/*
 * (éå½å®ç°)æ¥æ¾"äºåæ x"ä¸­é®å¼ä¸ºkeyçèç¹
 */
private BSTNode<T> search(BSTNode<T> x, T key) {
    if (x==null)
        return x;

    int cmp = key.compareTo(x.key);
    if (cmp < 0)
        return search(x.left, key);
    else if (cmp > 0)
        return search(x.right, key);
    else
        return x;
}

public BSTNode<T> search(T key) {
    return search(mRoot, key);
}
```

- ééå½çæ¬çä»£ç 

```java
/*
 * (ééå½å®ç°)æ¥æ¾"äºåæ x"ä¸­é®å¼ä¸ºkeyçèç¹
 */
private BSTNode<T> iterativeSearch(BSTNode<T> x, T key) {
    while (x!=null) {
        int cmp = key.compareTo(x.key);

        if (cmp < 0) 
            x = x.left;
        else if (cmp > 0) 
            x = x.right;
        else
            return x;
    }

    return x;
}

public BSTNode<T> iterativeSearch(T key) {
    return iterativeSearch(mRoot, key);
}
```

### æå¤§å¼åæå°å¼

![alg-tree-11](Images/alg-tree-11.png)



- æ¥æ¾æå¤§ç»ç¹

```java
/* 
 * æ¥æ¾æå¤§ç»ç¹: è¿åtreeä¸ºæ ¹ç»ç¹çäºåæ çæå¤§ç»ç¹ã
 */
private BSTNode<T> maximum(BSTNode<T> tree) {
    if (tree == null)
        return null;

    while(tree.right != null)
        tree = tree.right;
    return tree;
}

public T maximum() {
    BSTNode<T> p = maximum(mRoot);
    if (p != null)
        return p.key;

    return null;
}
```

- æ¥æ¾æå°ç»ç¹

```java
/* 
 * æ¥æ¾æå°ç»ç¹: è¿åtreeä¸ºæ ¹ç»ç¹çäºåæ çæå°ç»ç¹ã
 */
private BSTNode<T> minimum(BSTNode<T> tree) {
    if (tree == null)
        return null;

    while(tree.left != null)
        tree = tree.left;
    return tree;
}

public T minimum() {
    BSTNode<T> p = minimum(mRoot);
    if (p != null)
        return p.key;

    return null;
}
```

### åé©±ååç»§

èç¹çåé©±: æ¯è¯¥èç¹çå·¦å­æ ä¸­çæå¤§èç¹ã èç¹çåç»§: æ¯è¯¥èç¹çå³å­æ ä¸­çæå°èç¹ã

- æ¥æ¾åé©±èç¹

```java
/* 
 * æ¾ç»ç¹(x)çåé©±ç»ç¹ãå³ï¼æ¥æ¾"äºåæ ä¸­æ°æ®å¼å°äºè¯¥ç»ç¹"ç"æå¤§ç»ç¹"ã
 */
public BSTNode<T> predecessor(BSTNode<T> x) {
    // å¦æxå­å¨å·¦å­©å­ï¼å"xçåé©±ç»ç¹"ä¸º "ä»¥å¶å·¦å­©å­ä¸ºæ ¹çå­æ çæå¤§ç»ç¹"ã
    if (x.left != null)
        return maximum(x.left);

    // å¦æxæ²¡æå·¦å­©å­ãåxæä»¥ä¸ä¸¤ç§å¯è½: 
    // (01) xæ¯"ä¸ä¸ªå³å­©å­"ï¼å"xçåé©±ç»ç¹"ä¸º "å®çç¶ç»ç¹"ã
    // (01) xæ¯"ä¸ä¸ªå·¦å­©å­"ï¼åæ¥æ¾"xçæä½çç¶ç»ç¹ï¼å¹¶ä¸è¯¥ç¶ç»ç¹è¦å·æå³å­©å­"ï¼æ¾å°çè¿ä¸ª"æä½çç¶ç»ç¹"å°±æ¯"xçåé©±ç»ç¹"ã
    BSTNode<T> y = x.parent;
    while ((y!=null) && (x==y.left)) {
        x = y;
        y = y.parent;
    }

    return y;
}
```

- æ¥æ¾åç»§èç¹

```java
/* 
 * æ¾ç»ç¹(x)çåç»§ç»ç¹ãå³ï¼æ¥æ¾"äºåæ ä¸­æ°æ®å¼å¤§äºè¯¥ç»ç¹"ç"æå°ç»ç¹"ã
 */
public BSTNode<T> successor(BSTNode<T> x) {
    // å¦æxå­å¨å³å­©å­ï¼å"xçåç»§ç»ç¹"ä¸º "ä»¥å¶å³å­©å­ä¸ºæ ¹çå­æ çæå°ç»ç¹"ã
    if (x.right != null)
        return minimum(x.right);

    // å¦æxæ²¡æå³å­©å­ãåxæä»¥ä¸ä¸¤ç§å¯è½: 
    // (01) xæ¯"ä¸ä¸ªå·¦å­©å­"ï¼å"xçåç»§ç»ç¹"ä¸º "å®çç¶ç»ç¹"ã
    // (02) xæ¯"ä¸ä¸ªå³å­©å­"ï¼åæ¥æ¾"xçæä½çç¶ç»ç¹ï¼å¹¶ä¸è¯¥ç¶ç»ç¹è¦å·æå·¦å­©å­"ï¼æ¾å°çè¿ä¸ª"æä½çç¶ç»ç¹"å°±æ¯"xçåç»§ç»ç¹"ã
    BSTNode<T> y = x.parent;
    while ((y!=null) && (x==y.right)) {
        x = y;
        y = y.parent;
    }

    return y;
}
```

### æå¥

![alg-tree-8](Images/alg-tree-8.png)

```java
/* 
 * å°ç»ç¹æå¥å°äºåæ ä¸­
 *
 * åæ°è¯´æ: 
 *     tree äºåæ ç
 *     z æå¥çç»ç¹
 */
private void insert(BSTree<T> bst, BSTNode<T> z) {
    int cmp;
    BSTNode<T> y = null;
    BSTNode<T> x = bst.mRoot;

    // æ¥æ¾zçæå¥ä½ç½®
    while (x != null) {
        y = x;
        cmp = z.key.compareTo(x.key);
        if (cmp < 0)
            x = x.left;
        else
            x = x.right;
    }

    z.parent = y;
    if (y==null)
        bst.mRoot = z;
    else {
        cmp = z.key.compareTo(y.key);
        if (cmp < 0)
            y.left = z;
        else
            y.right = z;
    }
}

/* 
 * æ°å»ºç»ç¹(key)ï¼å¹¶å°å¶æå¥å°äºåæ ä¸­
 *
 * åæ°è¯´æ: 
 *     tree äºåæ çæ ¹ç»ç¹
 *     key æå¥ç»ç¹çé®å¼
 */
public void insert(T key) {
    BSTNode<T> z=new BSTNode<T>(key,null,null,null);

    // å¦ææ°å»ºç»ç¹å¤±è´¥ï¼åè¿åã
    if (z != null)
        insert(this, z);
}
```

### å é¤

![alg-tree-10](Images/alg-tree-10.png)



```java
/* 
 * å é¤ç»ç¹(z)ï¼å¹¶è¿åè¢«å é¤çç»ç¹
 *
 * åæ°è¯´æ: 
 *     bst äºåæ 
 *     z å é¤çç»ç¹
 */
private BSTNode<T> remove(BSTree<T> bst, BSTNode<T> z) {
    BSTNode<T> x=null;
    BSTNode<T> y=null;

    if ((z.left == null) || (z.right == null) )
        y = z;
    else
        y = successor(z);

    if (y.left != null)
        x = y.left;
    else
        x = y.right;

    if (x != null)
        x.parent = y.parent;

    if (y.parent == null)
        bst.mRoot = x;
    else if (y == y.parent.left)
        y.parent.left = x;
    else
        y.parent.right = x;

    if (y != z) 
        z.key = y.key;

    return y;
}

/* 
 * å é¤ç»ç¹(z)ï¼å¹¶è¿åè¢«å é¤çç»ç¹
 *
 * åæ°è¯´æ: 
 *     tree äºåæ çæ ¹ç»ç¹
 *     z å é¤çç»ç¹
 */
public void remove(T key) {
    BSTNode<T> z, node; 

    if ((z = search(mRoot, key)) != null)
        if ( (node = remove(this, z)) != null)
            node = null;
}
```

### æå°

```java
/*
 * æå°"äºåæ¥æ¾æ "
 *
 * key        -- èç¹çé®å¼ 
 * direction  --  0ï¼è¡¨ç¤ºè¯¥èç¹æ¯æ ¹èç¹;
 *               -1ï¼è¡¨ç¤ºè¯¥èç¹æ¯å®çç¶ç»ç¹çå·¦å­©å­;
 *                1ï¼è¡¨ç¤ºè¯¥èç¹æ¯å®çç¶ç»ç¹çå³å­©å­ã
 */
private void print(BSTNode<T> tree, T key, int direction) {

    if(tree != null) {

        if(direction==0)    // treeæ¯æ ¹èç¹
            System.out.printf("%2d is root\n", tree.key);
        else                // treeæ¯åæ¯èç¹
            System.out.printf("%2d is %2d's %6s child\n", tree.key, key, direction==1?"right" : "left");

        print(tree.left, tree.key, -1);
        print(tree.right,tree.key,  1);
    }
}

public void print() {
    if (mRoot != null)
        print(mRoot, mRoot.key, 0);
}
```

### éæ¯

```java
/*
 * éæ¯äºåæ 
 */
private void destroy(BSTNode<T> tree) {
    if (tree==null)
        return ;

    if (tree.left != null)
        destroy(tree.left);
    if (tree.right != null)
        destroy(tree.right);

    tree=null;
}

public void clear() {
    destroy(mRoot);
    mRoot = null;
}
```



## æµè¯ç¨åº

ä¸é¢å¯¹æµè¯ç¨åºçæµç¨è¿è¡åæï¼

- æ°å»º"äºåæ¥æ¾æ "rootã
- åäºåæ¥æ¾æ ä¸­ä¾æ¬¡æå¥1,5,4,3,2,6 ãå¦ä¸å¾æç¤º:

![alg-tree-bst-test-1](Images/alg-tree-bst-test-1.jpg)

- éååæ¥æ¾

æå¥1,5,4,3,2,6ä¹åï¼å¾å°çäºåæ¥æ¾æ å¦ä¸:

![alg-tree-bst-test-2](Images/alg-tree-bst-test-2.jpg)

```html
ååºéåç»æ: 1 5 4 3 2 6 
ä¸­åºéåç»æ: 1 2 3 4 5 6 
ååºéåç»æ: 2 3 4 6 5 1 
æå°å¼æ¯1ï¼èæå¤§å¼æ¯6ã
```

- å é¤èç¹4ãå¦ä¸å¾æç¤º:

![alg-tree-bst-test-3](Images/alg-tree-bst-test-3.jpg)



- éæ°éåè¯¥äºåæ¥æ¾æ ã

ä¸­åºéåç»æ: 1 2 4 5 6

## ä»£ç åæµè¯ä»£ç 

### ä»£ç å®ç°

```java
/**
 * Java è¯­è¨: äºåæ¥æ¾æ 
 *
 * @author skywang
 * @date 2013/11/07
 */

public class BSTree<T extends Comparable<T>> {

    private BSTNode<T> mRoot;    // æ ¹ç»ç¹

    public class BSTNode<T extends Comparable<T>> {
        T key;                // å³é®å­(é®å¼)
        BSTNode<T> left;    // å·¦å­©å­
        BSTNode<T> right;    // å³å­©å­
        BSTNode<T> parent;    // ç¶ç»ç¹

        public BSTNode(T key, BSTNode<T> parent, BSTNode<T> left, BSTNode<T> right) {
            this.key = key;
            this.parent = parent;
            this.left = left;
            this.right = right;
        }

        public T getKey() {
            return key;
        }

        public String toString() {
            return "key:"+key;
        }
    }

    public BSTree() {
        mRoot=null;
    }

    /*
     * ååºéå"äºåæ "
     */
    private void preOrder(BSTNode<T> tree) {
        if(tree != null) {
            System.out.print(tree.key+" ");
            preOrder(tree.left);
            preOrder(tree.right);
        }
    }

    public void preOrder() {
        preOrder(mRoot);
    }

    /*
     * ä¸­åºéå"äºåæ "
     */
    private void inOrder(BSTNode<T> tree) {
        if(tree != null) {
            inOrder(tree.left);
            System.out.print(tree.key+" ");
            inOrder(tree.right);
        }
    }

    public void inOrder() {
        inOrder(mRoot);
    }


    /*
     * ååºéå"äºåæ "
     */
    private void postOrder(BSTNode<T> tree) {
        if(tree != null)
        {
            postOrder(tree.left);
            postOrder(tree.right);
            System.out.print(tree.key+" ");
        }
    }

    public void postOrder() {
        postOrder(mRoot);
    }


    /*
     * (éå½å®ç°)æ¥æ¾"äºåæ x"ä¸­é®å¼ä¸ºkeyçèç¹
     */
    private BSTNode<T> search(BSTNode<T> x, T key) {
        if (x==null)
            return x;

        int cmp = key.compareTo(x.key);
        if (cmp < 0)
            return search(x.left, key);
        else if (cmp > 0)
            return search(x.right, key);
        else
            return x;
    }

    public BSTNode<T> search(T key) {
        return search(mRoot, key);
    }

    /*
     * (ééå½å®ç°)æ¥æ¾"äºåæ x"ä¸­é®å¼ä¸ºkeyçèç¹
     */
    private BSTNode<T> iterativeSearch(BSTNode<T> x, T key) {
        while (x!=null) {
            int cmp = key.compareTo(x.key);

            if (cmp < 0) 
                x = x.left;
            else if (cmp > 0) 
                x = x.right;
            else
                return x;
        }

        return x;
    }

    public BSTNode<T> iterativeSearch(T key) {
        return iterativeSearch(mRoot, key);
    }

    /* 
     * æ¥æ¾æå°ç»ç¹: è¿åtreeä¸ºæ ¹ç»ç¹çäºåæ çæå°ç»ç¹ã
     */
    private BSTNode<T> minimum(BSTNode<T> tree) {
        if (tree == null)
            return null;

        while(tree.left != null)
            tree = tree.left;
        return tree;
    }

    public T minimum() {
        BSTNode<T> p = minimum(mRoot);
        if (p != null)
            return p.key;

        return null;
    }
     
    /* 
     * æ¥æ¾æå¤§ç»ç¹: è¿åtreeä¸ºæ ¹ç»ç¹çäºåæ çæå¤§ç»ç¹ã
     */
    private BSTNode<T> maximum(BSTNode<T> tree) {
        if (tree == null)
            return null;

        while(tree.right != null)
            tree = tree.right;
        return tree;
    }

    public T maximum() {
        BSTNode<T> p = maximum(mRoot);
        if (p != null)
            return p.key;

        return null;
    }

    /* 
     * æ¾ç»ç¹(x)çåç»§ç»ç¹ãå³ï¼æ¥æ¾"äºåæ ä¸­æ°æ®å¼å¤§äºè¯¥ç»ç¹"ç"æå°ç»ç¹"ã
     */
    public BSTNode<T> successor(BSTNode<T> x) {
        // å¦æxå­å¨å³å­©å­ï¼å"xçåç»§ç»ç¹"ä¸º "ä»¥å¶å³å­©å­ä¸ºæ ¹çå­æ çæå°ç»ç¹"ã
        if (x.right != null)
            return minimum(x.right);

        // å¦æxæ²¡æå³å­©å­ãåxæä»¥ä¸ä¸¤ç§å¯è½: 
        // (01) xæ¯"ä¸ä¸ªå·¦å­©å­"ï¼å"xçåç»§ç»ç¹"ä¸º "å®çç¶ç»ç¹"ã
        // (02) xæ¯"ä¸ä¸ªå³å­©å­"ï¼åæ¥æ¾"xçæä½çç¶ç»ç¹ï¼å¹¶ä¸è¯¥ç¶ç»ç¹è¦å·æå·¦å­©å­"ï¼æ¾å°çè¿ä¸ª"æä½çç¶ç»ç¹"å°±æ¯"xçåç»§ç»ç¹"ã
        BSTNode<T> y = x.parent;
        while ((y!=null) && (x==y.right)) {
            x = y;
            y = y.parent;
        }

        return y;
    }
     
    /* 
     * æ¾ç»ç¹(x)çåé©±ç»ç¹ãå³ï¼æ¥æ¾"äºåæ ä¸­æ°æ®å¼å°äºè¯¥ç»ç¹"ç"æå¤§ç»ç¹"ã
     */
    public BSTNode<T> predecessor(BSTNode<T> x) {
        // å¦æxå­å¨å·¦å­©å­ï¼å"xçåé©±ç»ç¹"ä¸º "ä»¥å¶å·¦å­©å­ä¸ºæ ¹çå­æ çæå¤§ç»ç¹"ã
        if (x.left != null)
            return maximum(x.left);

        // å¦æxæ²¡æå·¦å­©å­ãåxæä»¥ä¸ä¸¤ç§å¯è½: 
        // (01) xæ¯"ä¸ä¸ªå³å­©å­"ï¼å"xçåé©±ç»ç¹"ä¸º "å®çç¶ç»ç¹"ã
        // (01) xæ¯"ä¸ä¸ªå·¦å­©å­"ï¼åæ¥æ¾"xçæä½çç¶ç»ç¹ï¼å¹¶ä¸è¯¥ç¶ç»ç¹è¦å·æå³å­©å­"ï¼æ¾å°çè¿ä¸ª"æä½çç¶ç»ç¹"å°±æ¯"xçåé©±ç»ç¹"ã
        BSTNode<T> y = x.parent;
        while ((y!=null) && (x==y.left)) {
            x = y;
            y = y.parent;
        }

        return y;
    }

    /* 
     * å°ç»ç¹æå¥å°äºåæ ä¸­
     *
     * åæ°è¯´æ: 
     *     tree äºåæ ç
     *     z æå¥çç»ç¹
     */
    private void insert(BSTree<T> bst, BSTNode<T> z) {
        int cmp;
        BSTNode<T> y = null;
        BSTNode<T> x = bst.mRoot;

        // æ¥æ¾zçæå¥ä½ç½®
        while (x != null) {
            y = x;
            cmp = z.key.compareTo(x.key);
            if (cmp < 0)
                x = x.left;
            else
                x = x.right;
        }

        z.parent = y;
        if (y==null)
            bst.mRoot = z;
        else {
            cmp = z.key.compareTo(y.key);
            if (cmp < 0)
                y.left = z;
            else
                y.right = z;
        }
    }

    /* 
     * æ°å»ºç»ç¹(key)ï¼å¹¶å°å¶æå¥å°äºåæ ä¸­
     *
     * åæ°è¯´æ: 
     *     tree äºåæ çæ ¹ç»ç¹
     *     key æå¥ç»ç¹çé®å¼
     */
    public void insert(T key) {
        BSTNode<T> z=new BSTNode<T>(key,null,null,null);

        // å¦ææ°å»ºç»ç¹å¤±è´¥ï¼åè¿åã
        if (z != null)
            insert(this, z);
    }

    /* 
     * å é¤ç»ç¹(z)ï¼å¹¶è¿åè¢«å é¤çç»ç¹
     *
     * åæ°è¯´æ: 
     *     bst äºåæ 
     *     z å é¤çç»ç¹
     */
    private BSTNode<T> remove(BSTree<T> bst, BSTNode<T> z) {
        BSTNode<T> x=null;
        BSTNode<T> y=null;

        if ((z.left == null) || (z.right == null) )
            y = z;
        else
            y = successor(z);

        if (y.left != null)
            x = y.left;
        else
            x = y.right;

        if (x != null)
            x.parent = y.parent;

        if (y.parent == null)
            bst.mRoot = x;
        else if (y == y.parent.left)
            y.parent.left = x;
        else
            y.parent.right = x;

        if (y != z) 
            z.key = y.key;

        return y;
    }

    /* 
     * å é¤ç»ç¹(z)ï¼å¹¶è¿åè¢«å é¤çç»ç¹
     *
     * åæ°è¯´æ: 
     *     tree äºåæ çæ ¹ç»ç¹
     *     z å é¤çç»ç¹
     */
    public void remove(T key) {
        BSTNode<T> z, node; 

        if ((z = search(mRoot, key)) != null)
            if ( (node = remove(this, z)) != null)
                node = null;
    }

    /*
     * éæ¯äºåæ 
     */
    private void destroy(BSTNode<T> tree) {
        if (tree==null)
            return ;

        if (tree.left != null)
            destroy(tree.left);
        if (tree.right != null)
            destroy(tree.right);

        tree=null;
    }

    public void clear() {
        destroy(mRoot);
        mRoot = null;
    }

    /*
     * æå°"äºåæ¥æ¾æ "
     *
     * key        -- èç¹çé®å¼ 
     * direction  --  0ï¼è¡¨ç¤ºè¯¥èç¹æ¯æ ¹èç¹;
     *               -1ï¼è¡¨ç¤ºè¯¥èç¹æ¯å®çç¶ç»ç¹çå·¦å­©å­;
     *                1ï¼è¡¨ç¤ºè¯¥èç¹æ¯å®çç¶ç»ç¹çå³å­©å­ã
     */
    private void print(BSTNode<T> tree, T key, int direction) {

        if(tree != null) {

            if(direction==0)    // treeæ¯æ ¹èç¹
                System.out.printf("%2d is root\n", tree.key);
            else                // treeæ¯åæ¯èç¹
                System.out.printf("%2d is %2d's %6s child\n", tree.key, key, direction==1?"right" : "left");

            print(tree.left, tree.key, -1);
            print(tree.right,tree.key,  1);
        }
    }

    public void print() {
        if (mRoot != null)
            print(mRoot, mRoot.key, 0);
    }
}
```

### æµè¯ä»£ç 

```java
/**
 * Java è¯­è¨: äºåæ¥æ¾æ 
 *
 * @author skywang
 * @date 2013/11/07
 */
public class BSTreeTest {

    private static final int arr[] = {1,5,4,3,2,6};

    public static void main(String[] args) {
        int i, ilen;
        BSTree<Integer> tree=new BSTree<Integer>();

        System.out.print("== ä¾æ¬¡æ·»å : ");
        ilen = arr.length;
        for(i=0; i<ilen; i++) {
            System.out.print(arr[i]+" ");
            tree.insert(arr[i]);
        }

        System.out.print("\n== ååºéå: ");
        tree.preOrder();

        System.out.print("\n== ä¸­åºéå: ");
        tree.inOrder();

        System.out.print("\n== ååºéå: ");
        tree.postOrder();
        System.out.println();

        System.out.println("== æå°å¼: "+ tree.minimum());
        System.out.println("== æå¤§å¼: "+ tree.maximum());
        System.out.println("== æ çè¯¦ç»ä¿¡æ¯: ");
        tree.print();

        System.out.print("\n== å é¤æ ¹èç¹: "+ arr[3]);
        tree.remove(arr[3]);

        System.out.print("\n== ä¸­åºéå: ");
        tree.inOrder();
        System.out.println();

        // éæ¯äºåæ 
        tree.clear();
    }
}
```

### æµè¯ç»æ

```java
== ä¾æ¬¡æ·»å : 1 5 4 3 2 6 
== ååºéå: 1 5 4 3 2 6 
== ä¸­åºéå: 1 2 3 4 5 6 
== ååºéå: 2 3 4 6 5 1 
== æå°å¼: 1
== æå¤§å¼: 6
== æ çè¯¦ç»ä¿¡æ¯: 
is root
is  1's  right child
is  5's   left child
is  4's   left child
is  3's   left child
is  5's  right child

== å é¤æ ¹èç¹: 3
== ä¸­åºéå: 1 2 4 5 6
```

## BSTç¸å³é¢ç®

äºåæ¥æ¾æ (BST): æ ¹èç¹å¤§äºç­äºå·¦å­æ ææèç¹ï¼å°äºç­äºå³å­æ ææèç¹ã

äºåæ¥æ¾æ ä¸­åºéåæåºã

**ä¿®åªäºåæ¥æ¾æ **

```html
Input:

    3
   / \
  0   4
   \
    2
   /
  1

  L = 1
  R = 3

Output:

      3
     /
   2
  /
 1
```

é¢ç®æè¿°: åªä¿çå¼å¨ L ~ R ä¹é´çèç¹

**å¯»æ¾äºåæ¥æ¾æ çç¬¬ k ä¸ªåç´ **

ä¸­åºéåè§£æ³:

```java
private int cnt = 0;
private int val;

public int kthSmallest(TreeNode root, int k) {
    inOrder(root, k);
    return val;
}

private void inOrder(TreeNode node, int k) {
    if (node == null) return;
    inOrder(node.left, k);
    cnt++;
    if (cnt == k) {
        val = node.val;
        return;
    }
    inOrder(node.right, k);
}
```

éå½è§£æ³:

```java
public int kthSmallest(TreeNode root, int k) {
    int leftCnt = count(root.left);
    if (leftCnt == k - 1) return root.val;
    if (leftCnt > k - 1) return kthSmallest(root.left, k);
    return kthSmallest(root.right, k - leftCnt - 1);
}

private int count(TreeNode node) {
    if (node == null) return 0;
    return 1 + count(node.left) + count(node.right);
}
```

**æäºåæ¥æ¾æ æ¯ä¸ªèç¹çå¼é½å ä¸æ¯å®å¤§çèç¹çå¼**

```html
Input: The root of a Binary Search Tree like this:

              5
            /   \
           2     13

Output: The root of a Greater Tree like this:

             18
            /   \
          20     13
```

åéåå³å­æ ã

```java
private int sum = 0;

public TreeNode convertBST(TreeNode root) {
    traver(root);
    return root;
}

private void traver(TreeNode node) {
    if (node == null) return;
    traver(node.right);
    sum += node.val;
    node.val = sum;
    traver(node.left);
}
```

**äºåæ¥æ¾æ çæè¿å¬å±ç¥å**

```html
        _______6______
      /                \
  ___2__             ___8__
 /      \           /      \
0        4         7        9
        /  \
       3   5

For example, the lowest common ancestor (LCA) of nodes 2 and 8 is 6. Another example is LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.
```

```java
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root.val > p.val && root.val > q.val) return lowestCommonAncestor(root.left, p, q);
    if (root.val < p.val && root.val < q.val) return lowestCommonAncestor(root.right, p, q);
    return root;
}
```

**äºåæ çæè¿å¬å±ç¥å**

```html
       _______3______
      /              \
  ___5__           ___1__
 /      \         /      \
6        2       0        8
        /  \
       7    4

For example, the lowest common ancestor (LCA) of nodes 5 and 1 is 3. Another example is LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.
```

```java
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null || root == p || root == q) return root;
    TreeNode left = lowestCommonAncestor(root.left, p, q);
    TreeNode right = lowestCommonAncestor(root.right, p, q);
    return left == null ? right : right == null ? left : root;
}
```

**ä»æåºæ°ç»ä¸­æé äºåæ¥æ¾æ **

```java
public TreeNode sortedArrayToBST(int[] nums) {
    return toBST(nums, 0, nums.length - 1);
}

private TreeNode toBST(int[] nums, int sIdx, int eIdx){
    if (sIdx > eIdx) return null;
    int mIdx = (sIdx + eIdx) / 2;
    TreeNode root = new TreeNode(nums[mIdx]);
    root.left =  toBST(nums, sIdx, mIdx - 1);
    root.right = toBST(nums, mIdx + 1, eIdx);
    return root;
}
```

**æ ¹æ®æåºé¾è¡¨æé å¹³è¡¡çäºåæ¥æ¾æ **

```html
Given the sorted linked list: [-10,-3,0,5,9],

One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:

      0
     / \
   -3   9
   /   /
 -10  5
```

```java
public TreeNode sortedListToBST(ListNode head) {
    if (head == null) return null;
    if (head.next == null) return new TreeNode(head.val);
    ListNode preMid = preMid(head);
    ListNode mid = preMid.next;
    preMid.next = null;  // æ­å¼é¾è¡¨
    TreeNode t = new TreeNode(mid.val);
    t.left = sortedListToBST(head);
    t.right = sortedListToBST(mid.next);
    return t;
}

private ListNode preMid(ListNode head) {
    ListNode slow = head, fast = head.next;
    ListNode pre = head;
    while (fast != null && fast.next != null) {
        pre = slow;
        slow = slow.next;
        fast = fast.next.next;
    }
    return pre;
}
```

**å¨äºåæ¥æ¾æ ä¸­å¯»æ¾ä¸¤ä¸ªèç¹ï¼ä½¿å®ä»¬çåä¸ºä¸ä¸ªç»å®å¼**

```html
Input:

    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

Output: True
```

ä½¿ç¨ä¸­åºéåå¾å°æåºæ°ç»ä¹åï¼åå©ç¨åæéå¯¹æ°ç»è¿è¡æ¥æ¾ã

åºè¯¥æ³¨æå°ï¼è¿ä¸é¢ä¸è½ç¨åå«å¨å·¦å³å­æ ä¸¤é¨åæ¥å¤çè¿ç§ææ³ï¼å ä¸ºä¸¤ä¸ªå¾æ±çèç¹å¯è½åå«å¨å·¦å³å­æ ä¸­ã

```java
public boolean findTarget(TreeNode root, int k) {
    List<Integer> nums = new ArrayList<>();
    inOrder(root, nums);
    int i = 0, j = nums.size() - 1;
    while (i < j) {
        int sum = nums.get(i) + nums.get(j);
        if (sum == k) return true;
        if (sum < k) i++;
        else j--;
    }
    return false;
}

private void inOrder(TreeNode root, List<Integer> nums) {
    if (root == null) return;
    inOrder(root.left, nums);
    nums.add(root.val);
    inOrder(root.right, nums);
}
```

**å¨äºåæ¥æ¾æ ä¸­æ¥æ¾ä¸¤ä¸ªèç¹ä¹å·®çæå°ç»å¯¹å¼**

```html
Input:

   1
    \
     3
    /
   2

Output:

1
```

å©ç¨äºåæ¥æ¾æ çä¸­åºéåä¸ºæåºçæ§è´¨ï¼è®¡ç®ä¸­åºéåä¸­ä¸´è¿çä¸¤ä¸ªèç¹ä¹å·®çç»å¯¹å¼ï¼åæå°å¼ã

```java
private int minDiff = Integer.MAX_VALUE;
private TreeNode preNode = null;

public int getMinimumDifference(TreeNode root) {
    inOrder(root);
    return minDiff;
}

private void inOrder(TreeNode node) {
    if (node == null) return;
    inOrder(node.left);
    if (preNode != null) minDiff = Math.min(minDiff, node.val - preNode.val);
    preNode = node;
    inOrder(node.right);
}
```

**å¯»æ¾äºåæ¥æ¾æ ä¸­åºç°æ¬¡æ°æå¤çå¼**

```html
   1
    \
     2
    /
   2

return [2].
```

ç­æ¡å¯è½ä¸æ­¢ä¸ä¸ªï¼ä¹å°±æ¯æå¤ä¸ªå¼åºç°çæ¬¡æ°ä¸æ ·å¤ã

```java
private int curCnt = 1;
private int maxCnt = 1;
private TreeNode preNode = null;

public int[] findMode(TreeNode root) {
    List<Integer> maxCntNums = new ArrayList<>();
    inOrder(root, maxCntNums);
    int[] ret = new int[maxCntNums.size()];
    int idx = 0;
    for (int num : maxCntNums) {
        ret[idx++] = num;
    }
    return ret;
}

private void inOrder(TreeNode node, List<Integer> nums) {
    if (node == null) return;
    inOrder(node.left, nums);
    if (preNode != null) {
        if (preNode.val == node.val) curCnt++;
        else curCnt = 1;
    }
    if (curCnt > maxCnt) {
        maxCnt = curCnt;
        nums.clear();
        nums.add(node.val);
    } else if (curCnt == maxCnt) {
        nums.add(node.val);
    }
    preNode = node;
    inOrder(node.right, nums);
}
```

