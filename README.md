# test_5_6
#include <stdio.h>
#include <stdlib.h>
//二叉树的顺序存储
#define MaxSize 100
struct TreeNode{
	Elemtype value;
	bool IsEmpty;
};
void testTree()
{
	TreeNode T[MaxSize];
	for(int i=0;i<MaxSize;i++)
    {
		T[i].IsEmpty = true;
	}
}
//二叉树的链式存储
typedef struct BiTNode{
	Elemtype data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
struct Eiemtype{
	int value;
};
void testTree()
{
	BiTree root = NULL;//定义一个二叉树
    //插入一个根结点
    root = (BiTree)malloc(sizeof(BiTNode));
	root->data = {1};
	root->lchild = NULL;
	root->rchild = NULL;
	//插入一个新结点
	BiTNode* p = (BiTNode*)malloc(sizeof(BiTNode));
	p->data = {2};
	p->lchild = NULL;
	p->rchild = NULL;
	root->lchild = p;
}
//二叉树的先序遍历
void PreOrder(BiTree T){
	if(T != NULL)
	{
		visit(T);
		PreOrder(T->lchild);
		PreOrder(T->rchild);
	}
}
//二叉树的中序遍历
void InOrder(BiTree T){
	if(T != NULL)
	{
		InOrder(T->lchild);
		visit(T);
		InOrder(T->rchild);
	}
}
//二叉树的后序遍历
void PostOrder(BiTree T){
	if(T != NULL)
	{
		PostOrder(T->lchild);
		PostOrder(T->rchild);
		visit(T);
	}
}
//求树的深度
int TreeDepth(BiTree T){
	if(T == NULL)
	{
		return 0;
	}
	else
	{
		int l = TreeDepth(T->lchild);
		int r = TreeDepth(T->rchild);
		return l>r? l : r;
	}
}
//二叉树的层序遍历
//链式队列结点
typedef struct LinkNode{
	BiTNode* data;
	struct LinkNode* next;
}LinkNode;
typedef struct{
	struct LinkNode *front,*rear;
}LinkQueue;
//二叉树的链式存储
typedef struct BiTNode{
	char data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
void LevelOrder(BiTree T){
	LinkQueue Q;
	InitQueue(Q);
	BiTree p;//定义一个头结点
	EnQueue(Q,T);//根结点入队
	while(!IsEmpty(Q))
	{
		DeQueue(Q,p);//队头结点出队
		visit(p);//访问队头结点
		if(p->lchild != NULL)
			EnQueue(Q,p->lchild);
		if(p->rchild != NULL)
			EnQueue(Q,p->rchild);
	}
}
