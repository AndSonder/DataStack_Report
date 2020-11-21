<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>
## 一、实验目的

1. 掌握二叉树的建立和遍历

2. 掌握二叉树遍历的应用

3. 掌握线索二叉树的建立和遍历

4. 掌握hufmman编码

## 二、实验内容

1. 递归建立和层次遍历二叉树

2. 二叉树的深度非递归遍历

3. 统计二叉树中右孩子节点的个数

4. 线索二叉树的建立和遍历

5. 哈夫曼编码

## 三、实验环境

​    在PTA平台进行实验

## 四、实验要求

​    根据每个实训的要求完成代码提交和测评

## 五、实验步骤

### 5.1 非递归建立和层次遍历二叉树

**二叉树的建立**

本题要求编写建立二叉树的函数和层次遍历二叉树的函数。

二叉树的建立方法有递归建立和非递归建立，在本题中我选择非递归法进行建立。设计思路如下：

**二叉树的层次遍历**

二叉树的层次遍历法使用队列这种算法，因为层次遍历的过程符合**先进先出**的特点。主要思路如下：

首先将根节点入栈，然后将队列不为空作为循环结束条件。每次的循环打印队头然后让队头出队。然后如果结点有左右孩子就将左右孩子依次入队，以此往复。**在后面的实验总结中我对层次遍历法进行更加详细的总结。**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201109134456785.png)

### 5.2 非递归方式统计二叉树中右孩子结点的个数

本题要求采用非递归方式统计二叉树中右孩子结点的个数。

**输入格式:**

这里采用递归方式建立二叉树，输入的先序序列

**输出格式:**

输出是二叉树右孩子结点的个数

本题要求使用非递归方式统计二叉树中右孩子的个数。本题的问题可以分解为两个部分：

1.**非递归遍历二叉树**

2.统计右孩子的数目

所以关键为使用非递归的方式遍历二叉树。

非递归遍历二叉树需要使用栈的数据结构

在进行非递归遍历二叉树时思路如下：

- 从根节点开始，将根结点压入栈中
- 如果栈不为空，从栈中取出第一个元素访问
- 如果p的右孩子不为空，入栈
- 如果p的左孩子不为空，入栈
- 重复一直到栈为空为止

因为栈具有**后进先出**的特点，而先序遍历的顺序为根左右，所以在代码当中先把右节点入栈，再把左结点入栈。

当遍历到的结点的右结点不为空时，将右孩子的数目加一。

### 5.3 二叉树的非递归遍历

本题要求采用栈实现对二叉树的非递归遍历，包括先序、中序和后序三种遍历方式。

在上题中也涉及到了二叉树的非递归遍历方式。但是二叉树的非递归建立方式主要有两种，上一题中使用的是第一种方式实现。但是如果想要使用非递归的方式实现二叉树的先序，中序和后序遍历。使用第二种方式更加适合，每种遍历方式需要修改的代码量不多，且算法的时间复杂度更低。

**先序遍历**

假设考虑只是右孩子入栈，左孩子沿着左分支深入，经过的时候就访问，不入栈。从根结点开始，沿着左分支深入、访问，并将结点的右孩子入栈，直到到达一个空结点。然后检查栈是否为空，栈空则结束，栈非空，出栈一个元素，重复上述过程。

**中序遍历**

从根节点开始，沿着左分支一直深入将结过的每一个结点入栈，直到到达一个空结点。然后出栈一个元素，并访问出栈的元素，接着进入出栈结点的右分支，此时检查出栈结点的右分支以及栈是否为空，如果都为空算法结束，否则重复上述过程

**后序遍历**

（1）如果左分支不空，则沿着左分支一直下行，经过的结点进栈，直到沿着左分支深入不下去时检查右分支，如果右分支不为空，接着进入右分支。重复上述过程。直到一个结点的左右都为空时访问该结点，称之为Now

（2）如果Now是父结点的左孩子，则继续进入父结点的右分支，重复（1）

（3）如果Now是父结点的右孩子，则说明父结点的左右结点均已经处理，返回上级的根结点，出栈访问。

（4）直到Now为空并且栈也为空结束。

### 5.4  线索二叉树的建立和遍历

本题要求实现对建立中序线索二叉树和中序遍历中序线索二叉树。

线索二叉树的建立和遍历我在实验总结中详细的写出了并且附上了相关代码。

### 5.5  哈夫曼编码

本题要求字符的哈夫曼编码，注意建立的哈夫曼树严格按照左小右次小的顺序，并且哈夫曼编码时严格按照左‘0’右‘1’进行编码。

本题的实现过程主要有2步：

1.将数据存入链表当中

2.根据链表中数据构造哈夫曼树

3.对哈夫曼树结构进行编码

本题中使用的结构体Node为：

```cpp
// CPP
typedef struct HuffNode {
    int weight; // 存储权重
    char name;  // 存储名字
    string code;// 储存编码
    HuffNode *next; // 存储下一个结构体的
    HuffNode *left; // 左孩子结点地址
    HuffNode *right;// 右孩子结点地址
} *huffNode;
```

通过构建哈夫曼树的代码如下，因为哈夫曼树的手动构造过程非常简单，所以本题主要还是结合代码进行说明

```cpp
huffNode CraeteHuff(huffNode huffLink) { // huffLink为上述构造出的链表，这里链表是有序的
    huffNode p1, p2;
    while (huffLink->next->next != nullptr) { // 确定循环的停止条件，除了头节点外只有一个有效结点了
      	// 取两个结点，就是手动计算中的找两个结点
        p1 = huffLink->next;
        p2 = huffLink->next->next;
        auto p3 = new struct HuffNode();
        p3->weight = p1->weight + p2->weight; // 构造出新的结点，并加入到链表当中
        p3->left = p1; // 小权重的作为左结点
        p3->right = p2; // 大结点的作为
      	// 在原链表当中删除p1和p2
        huffLink->next = huffLink->next->next->next;
      	// 将新的结点插入到链表当中，需要保持链表的有序性。
        orderInsert(huffLink, p3);
    }
    return huffLink->next;
}
```

接下来对元素进行编码，主要的思路就是在遍历元素的过程中更新HuffNode中的code，使用递归的方式进行遍历即可

```cpp
map<char, string> huffResult; // 将结过储存到map当中
void huffEncode(huffNode huffTree) {
    if (huffTree->left == nullptr and huffTree->right == nullptr) {
        huffResult[huffTree->name] = huffTree->code; // 到根节点了
    }
    if (huffTree->left != nullptr) {
        huffTree->left->code = huffTree->code + '0'; // 进入左结点，往左加0
        huffEncode(huffTree->left);
    }
    if (huffTree->right != nullptr) {
        huffTree->right->code = huffTree->code + '1'; // 进入右结点，往右加1
        huffEncode(huffTree->right);
    }
}
```

## 6 实验总结

本次对二叉树的各种知识点进行了详细的总结。写总结的过程中主要参考大话数据结构这本书籍。虽然大多数内容和书上的内容差不多，但是每个字都是我一个一个敲上去的。也结合了书本的知识。我还将总结发到了博客上，链接：https://blog.csdn.net/python_LC_nohtyp/article/details/109565416 

- 因为我是在CSDN里写了之后导出的，所以图片的右下脚会带有一些水印

### 6.1 二叉树的一些性质

- 二叉树中，第i层最多有$2^{i-1}$个节点
- 如果二叉树的深度为K，那么此二叉树最多有$2^{K}-1$个结点
- 二叉树中，终端结点数（叶子结点树）为$n_0$,度为2的结点树为$n_2$，则$n_0 = n_2 + 1$.

### 6.2 两种特殊的二叉树

#### 6.2.1 满二叉树

除了叶子结点，每个结点的度都为2，则此二叉树称为满二叉树.

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231219703.png)

如图所示就是一棵满二叉树;

满二叉树除了满足普通二叉树的性质，还具有以下性质：
- 满二叉树中第$n$层的节点数为$2^n-1$ 个。
- 深度为 k 的满二叉树必有 $2^k - 1$ 个节点 ，叶子数为 $2^k-1$。
- 满二叉树中不存在度为 1 的节点，每一个分支点中都两棵深度相同的子树，且叶子节点都在最底层。
具有 $n$ 个节点的满二叉树的深度为 $log_2(n+1)$。

#### 6.2.2 完全二叉树

如果二叉树中除去最后一层节点为满二叉树，且最后一层的结点依次从左到右分布，则此二叉树被称为`完全二叉树`。

<img src="%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231219654.png" alt="在这里插入图片描述" style="zoom:67%;" />

完全二叉树除了具有普通二叉树的性质，它自身也具有一些独特的性质，比如说，n 个结点的完全二叉树的深度为 ⌊log2n⌋+1。

**⌊log2n⌋ 表示取小于 log2n 的最大整数。例如，⌊log24⌋ = 2，而 ⌊log25⌋ 结果也是 2。**

### 6.3 二叉树的存储结构

#### 6.3.1 二叉树的顺序存储结构

就是用一维数组存储二叉树中的结点，并且结点的存储位置，也就是数组的下标要能体现结点之间的逻辑关系，比如双亲与孩子的关系，左右兄弟的关系等。

一颗完全二叉树如下图所示：

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231219860.png)

将这颗二叉树存入数组中，相应的下标对应相同的位置，如图所示：
<img src="%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/20201108221536204.png" alt="在这里插入图片描述" style="zoom:67%;" />
**由于完全二叉树的严格定义，所以用顺序结构也可以表现出二叉树的结构来。**

当然对于一般的二叉树，尽管层序编号不能反应逻辑关系，但是可以将其按照完全二叉树编号，只不过，把不存在的结点设置为$\Lambda$而已。如图注意浅色结点表示不存在。

<img src="%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231220113-5280340.png" alt="在这里插入图片描述" style="zoom:67%;" />


**顺序存储结构只适用于完全二叉树，用于其他树的类型会造成比较大的空间浪费**

#### 6.3.2 二叉树的链式存储

既然顺序存储适用性不强，我们就需要考虑链式存储结构，二叉树每个结点最多有两个孩子，所以为它设计一个数据域和指针域。我们称这样的链表为**二叉链表**

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/20201108224945399.png)
以下树二叉树链表的结点结构定义代码：
```c
typedef char DateType;

typedef struct BitNode {
    DateType data;
    struct BitNode *leftChird, *rightChird;
};

typedef struct BitNode *BiTree;
```
<img src="%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231219817.png" alt="在这里插入图片描述" style="zoom:67%;" />

### 6.4 遍历二叉树

二叉树的遍历函数有很多种，主要可以分为一下四种：

#### 6.4.1 四种遍历方式

##### 前序遍历

若二叉树为空，则空操作返回，否则先访问根结点，然后前序遍历左子树，再前序遍历右子树。 也就是 **根左右** 【根在第一个】

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231219824.png)

##### 中序遍历

顺序为：左根右 【根在第二个】

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231219879.png)

##### 后序遍历

顺序为：左右根 【根在第三个】

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/20201108230408240.png)
##### 层序遍历

规则树若树为空，则空操作返回，否则从树的第一层，也就是根节点开始访问，从上而下逐层遍历，在同一层中，按从左到右的顺序对结点以此访问。

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/20201108230901341.png)

那么为什么需要那么多种遍历算法呢？
我们使用图像的方式来表现树的结构，应该说是非常简单直观和容易理解，但是对于计算机来说，它只有循环，判断等方式来处理，也就是说，它只会处理线性序列而我们刚才提到的四种遍历方法，其实都是把树中的结点变成某种意义的线性序列，这就给程序的实现带来了好处。

#### 6.4.2 遍历算法

##### 递归遍历

二叉树的定义是采用递归的方式，所以，实现遍历算法也可以采用递归，而且极其的简介明了。

```cpp
// 二叉树的前序遍历递归算法
void PreOrderTraverse(BiTree T){
    if (T == nullptr)
        return;
    cout << T->data; // 打印数据
    PreOrderTraverse(T->leftChird); // 先遍历左子树
    PreOrderTraverse(T->rightChird); // 再遍历右子树
}
```

中序遍历和后序遍历的算法在代码上都是极为相似的，我们可以将其合写为一个函数然后通过一个遍历mode来选择使用哪一种算法。

```cpp
// 二叉树前中后序遍历递归算法合写
void BiTraverse(BiTree T,int mode){ // 通过mode来控制
    if (T == nullptr)
        return;
    if (mode == 0) cout << T->data; // 前序遍历
    PreOrderTraverse(T->leftChird); // 先遍历左子树
    if (mode == 1) cout << T->data; // 中序遍历
    PreOrderTraverse(T->rightChird); // 再遍历右子树
    if (mode == 2) cout << T->data; // 后序遍历
}
```

##### 层次遍历法


```cpp
// 二叉树层次遍历算法
void LevelOrder(BiTree T){
    BiTree p;
    queue<BiTree> Queue; // 创建空队列
    if (T == nullptr)
        return;
    p = T;
    Queue.push(T); // 根节点入队
    while (!Queue.empty()){ // 队列不空执行循环
        p = Queue.front();
        Queue.pop();
        cout << p->data;
        if (p->leftChird != nullptr)
            Queue.push(p->leftChird);
        if (p->rightChird != nullptr)
            Queue.push(p->rightChird);
    }
}
		
```
下图是程序在运行过程中的示意图：
![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231219981.png)
##### 非递归算法先序遍历二叉树

先序遍历二叉树的步骤如下：

- 从根结点bt开始，将根节点压入栈lstack中；
- 如果栈不为空，从栈lstack中弹出一个元素p，并访问；
- 如果p的右孩子不为空，入栈stack
- 如果p的左孩子不空，入栈stack
- 重复上述过程直到栈空

以下是实现代码：
```cpp
// 二叉树先序遍历非递归算法
void PreOrder_NRecursion1(BiTree bt)
{
    stack<BiTree> lstack;
    BitNode *p;
    lstack.push(bt); // 根节点入栈
    while (!lstack.empty()){
        p = lstack.top(); // 取出栈顶元素
        lstack.pop(); // 栈顶元素出栈
        cout << p->data;
        if (p->rightChird)
            lstack.push(p->rightChird);
        if (p->leftChird)
            lstack.push(p->leftChird);
    }
}
```

##### 推导遍历结果

有一种题目是给你前序遍历和中序遍历的结果让你写出后序遍历的结果，通过这种题目我们可以总结出二叉树遍历的性质。

- 已知前序遍历序列和中序遍历序列，可以唯一确定一颗二叉树
- 已知后序遍历序列和中序遍历序列，可以唯一确定一颗二叉树

### 6.5 建立二叉树

#### 6.5.1 扩展二叉树

我们在内存中建立一个如下面左图所示的二叉树，为了能让每个结点确认是否有左右孩子，我们对它进行扩展可以得到下面右图的结果，它的前序遍历序列就是AB#D##C##
![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231220223.png)
#### 6.5.2 二叉树的递归构建法

假设将前序遍历序列AB#D##C## 作为输入，则实现算法如下：
```cpp
// 二叉树的递归建立法
BiTree CreateBiTree(){
    DateType ch;
    BiTree T;
    cin >> ch;
    if (ch == '#')
        T = nullptr;
    else{
        T = new BitNode();
        T->data = ch;
        T->leftChird = CreateBiTree();
        T->rightChird = CreateBiTree();
    }
    return T;
}
```

#### 6.5.3 线索二叉树的建立

##### 二叉树说明

我们现在提倡节约型社会，一切都应该节约为本，对待程序我们当然也不例外，不能浪费时间和空间。想想我们上面建立的二叉树，建立了很多空的指针域，有许许多多的空指针域，所以这个应该想办法利用起来。

<img src="%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231220113.png" alt="在这里插入图片描述" style="zoom:67%;" />

对于一个有n个结点的二叉链表，每个结点有指向左右孩子的两个指针域，所以一共有2n个指针域。而n个结点的二叉树。一共有n-1条分支线数，也就是说，其实存在2n-（n-1）=n+1个空指针域。比如上图有10个结点，而带有“🈳️”指针域为11.这些空间不储存任何事物，白白的浪费着空间资源。
所以我们可以考虑利用那些空地址，存放指向结点在某种遍历次序下的前驱和后继结点。就好像GPS导航仪一样，我们开车的时候哪怕对具体目的地的位置一无所知，但它每次都可以告诉我从当前位置但下一步应该走向哪里。**这种指向前驱和后稷但指针称为线索**，加上线索但二叉链表称为线索链表，相应的二叉树称为线索二叉树。

请看下图，我们对这颗数进行中序遍历后，将所有对空指针域中对rightChird改为指向它对后继结点，于是我们就可以通过指针知道H对后继结点数D，I对后继是B，J对后继是E，E的后继是A，F的后继是C，G的后继结点为NULL，此时一共有6个空指针域被利用

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231220146.png)

接下来我们将这颗二叉树的所有空指针域中的leftChird，改为指向当前结点的前驱。因此H的前驱是NULL，I的前驱是D，J的前驱是B，F的前驱是A，G的前驱是C。一共5个空指针被利用，正好和上面的后继加起来是11个。

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231220145.png)

**其实线索二叉树，等于是把一颗二叉树变成了一个双向链表，这样对我们对插入删除结点、查找某个结点都带来了方便。所以我们对二叉树以某种次序遍历使其变成线索二叉树对过程称为线索化。**

但是问题并未有完全解决。我们如何知道某一个结点对leftChird是指向它对左孩子还是指向前驱呢？显然我们需要加上一个区分对标志。因此我们在每个结点再增设两个标志域ltag和rtag，如果ltag和rtag只是存放0或1数字对布尔形遍历，其占用对内存空间小于像leftChird和rightChird对指针变量。结点结构如下所示：
![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/20201110225833169.png)
- Itag为0时指向该结点对左孩子，为1时指向该结点对前驱。
- rtag为0时指向该结点对右孩子，为1时指向该结点对后继。
- 所以上图对二叉树可以修改为下图对样子；
![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231220439.png)
##### 线索二叉树的结构实现

二叉树线索存储结构定义代码如下：

```cpp
// 二叉树的二叉线序存储结构定义
typedef enum {Link,Thread} PointerTag; // Link == 0 表示指向左孩子指针，Thread == 1表示指向前驱或者后继的线索

typedef struct BiThrNode {
    DateType data;
    struct BiThrNode *leftChird,*rightChird;
    PointerTag LTag;
    PointerTag RTag;
} BiThrNode,*BiThrTree;
```

线索化的实质就是讲哦二叉链表中的空指针改为指向前驱或者后继的线索。由于前驱和后继的信息只有在遍历该二叉树时才能得到，所以线索化的过程就是在遍历的过程中修改空指针的过程

中序遍历线索化的递归代码如下：
```cpp
// 中序建立线索二叉树
BiThrTree pre; // 全局变量，始终指向刚刚访问过的结点

void InThreading(BiThrTree p)
{
    if (p)
    {
        InThreading(p->leftChird); // 递归左子树线索化
        if (!p->leftChird) // 没有左孩子
        {
            p->LTag = Thread; // 前驱线索
            p->leftChird = pre; // 左孩子指针指向前驱
        }
        if (!pre->rightChird) // 没有右孩子
        {
            pre->RTag=Thread; // 后继线索
            pre->rightChird = p; // 前驱右孩子指针指向后继
        }
    }
    pre = p;
    InThreading(p->rightChird);
}
```

可以发现就是多了添加前驱和后继的代码而已，其他都没有什么变化

if(!p->leftChird) 表示如果某结点的左指针域为空，因为其前驱结点刚刚访问过，赋值给了pre，所以看了眼将pre赋值给p->leftChird，并修改p->LTag = Thread 也就是定义为1，以完成前驱结点的线索化。

后继就要稍微麻烦一些，因为此时p结点的后继还没有访问到，因此只能对它的前驱结点pre的右指针rightChird做判断，if(!pre->rightChird) 表示如果为空，则p就是pre的后继，于是pre->rightChird=p,并且设置pre->RTag=Thread，完成后继结点的线索化。

完成前驱和后继结点的判断后，别忘记将当前的结点p赋值给pre，以便下一次使用。

有了线索二叉树后，我们对它进行遍历时发现，其实就等于是操作一个双向链表结构。


![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231220514.png)
```cpp
int InOrderTraverse_Thr(BiThrTree T)
{
    BiThrTree p;
    p = T->leftChird; // P指向根节点
    while (p != T) // 空树或者遍历结束
    {
        while (p->LTag == Link) // 当LTag==0时循环到中序序列第一个结点
            p = p->leftChird;
        cout << p->data; // 显示结点数据，可以更改为对其他结点操作
        while (p->RTag == Thread and p->rightChird != T)
        {
            p = p->rightChird;
            cout << p->data;
        }
        p = p->rightChird; // p进至其右子数结点
    }
    return 1;
}
```
由于它充分利用了空指针域对空间，又保证了创建时对一次遍历就可以使用前驱后继对信息，**所以在实际问题中，如果所用对二叉树需要
经常遍历或查找结点时需要某种遍历序列中对前驱和后继，那么采用线索二叉链表对存储结构是非常不错对选择**

### 6.6 树、森林与二叉树的转换

#### 6.6.1 树转换为二叉树

将树转换为二叉树的步骤如下：
1. 加线
2. 去线
3. 层次调整



<img src="%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/20201111210018457.png" alt="在这里插入图片描述" style="zoom:150%;" />

<img src="%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/20201111210036501.png" alt="在这里插入图片描述" style="zoom:150%;" />



#### 6.62 森林转化为二叉树

森林树由若干课树组成的，所以可以理解为，森林中的每一颗树都是兄弟，可以按照兄弟的处理办法来操作。步骤如下：
1. 把每个树转化为二叉树
2. 第一课二叉树不动，从第二颗二叉树开始，以此把后一颗二叉树的根节点作为前一个二叉树根结点的右孩子，用线连起来。但所有但二叉树连接起来后就得到你由森林转化来的二叉树。

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231220342.png)
#### 6.6.3 二叉树转化为森林

**如何判断一颗二叉树时候能够转化为一颗树还是森林？**
标准很简单，那就是只要看这颗二叉树的根结点有没有右孩子，有就是森林
步骤如下：
1. 从根节点开始，若右孩子存在，则把与右孩子结点的连线删除，再查看分离后的二叉树，若右孩子存在，则连线删除.... 直到所有的右孩子连线都删除为止，得到分离的二叉树。
2. 再将没课分离后的二叉树转化为树即可

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231220469.png)
### 6.7 哈夫曼树

哈夫曼研究出哈夫曼编码解决你当年远距离通信（主要是电报）的数据传输的最优化问题。
比如我们有一段文字内容为“BADCADFEED”要网络传输给别人，显然用二进制的数字（0和1）来表示是很自然的想法。我们现在这个文字只有六个字母ABCDEF，那么我们可以用相应的二进制数据表示，如下表所示：



| 字母       | A    | B    | C    | D    | E    | F    |
| ---------- | ---- | ---- | ---- | ---- | ---- | ---- |
| 二进制字符 | 000  | 001  | 010  | 011  | 100  | 101  |


这样真正传输的数据就是编码后的“001000011010000011101100100011”对方接收的时候可以按照3位一分来译码，如果一篇文章很长，这样的二进制串也不太方便，实际上无论是中文还是英文，几个元音字符“a e i o u”，中文中的“的  了   有  在”等汉字的出现频率极高。
假设六个字母的频率为A 27，B 8，C 15，D 15，E 30，F 5，合起来正好是100% 那意味着完全可以按照哈夫曼树来规划它们。
下面的左图为构造哈夫曼树的过程的权值显示。右图为将权值左分支改为0，右分支改为1后的哈夫曼树。

![在这里插入图片描述](%E5%8D%A2%E7%95%85%E7%AC%AC%E4%B8%89%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.assets/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3B5dGhvbl9MQ19ub2h0eXA=,size_16,color_FFFFFF,t_70-20201113231220378.png)

然后我们进行编码可以得到：

| 字母       | A    | B    | C    | D    | E    | F    |
| ---------- | ---- | ---- | ---- | ---- | ---- | ---- |
| 二进制字符 | 01   | 1001 | 101  | 00   | 11   | 1000 |

这样重新编码后要如何解码呢？
编码中非0即1，长度不等的话其实是很容易混淆的，所以**若要设计长短不等的编码，则必须是任一字符的编码都不是另一个字符的编码的前缀，这种编码称做前缀编码。**

可是仅仅这样还是不方便去解码，因此在解码时，还是要用到哈夫曼树，即发送方和接收方必须要约定好同样的哈夫曼规则。

















































































