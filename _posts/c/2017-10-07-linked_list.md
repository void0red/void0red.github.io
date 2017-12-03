---
title: "About learning linked_list"
date: 2017-10-24
tag: c
layout: post
---
> some Pointer and Struct practicing

链表由两部分组成，一部分是指针区，一部分是数据区，这里要说的是单链表，指针区仅仅只是下一个节点的地址，为了简化程序，数据区也只设置一个整型变量

```c
//初始化头节点
node * node_init(){
	node * head = (node *)malloc(sizeof(node));
	head -> next = NULL;
	head -> data = -1;
	return head;
}
//在链表末尾添加节点，返回节点指针
node * node_add(node *head, int data){
	node * newnode = (node *)malloc(sizeof(node));
	if(!newnode)return NULL;
	node *p = head;
	while(p -> next != NULL )p = p -> next;
	p -> next = newnode;
	newnode -> next = NULL;
	newnode -> data = data;
	return newnode;
}
//打印链表所有节点
void list_print(node *head){
	node *p = head;
	int x = 0;
	while(p != NULL){
		printf("node(%d):%d\n", x, p -> data);
		p = p -> next;
		x++;
	}
}
//在指定节点末尾插入新的节点（头节点为0号），返回节点指针
node * node_insert(node *head, int i,int data){
	node * newnode = (node *)malloc(sizeof(node));
	if(!newnode)return NULL;
	newnode -> data = data;
	node * p = head;
	while(i > 0 && p -> next != NULL){
		p = p -> next;
		i--;
	}
	newnode -> next = p -> next;
	p -> next = newnode;
	return newnode;
}
//删除指定节点（头节点为0号）
void node_del(node *head, int i){
	node *p1 = head;
	node *p2;
	if(i == 0)i++;
	while(i > 0 && p1 -> next != NULL){
		i--;
		p2 = p1;
		p1 = p1 -> next;
	}
	p2 -> next = p1 -> next;
	free(p1);
}
//返回链表的节点数
int list_length(node *head){
	node *p = head;
	int count = 0;
	while(p != NULL){
		p = p -> next;
		count++;
	}
	return count;
}
//删除链表
void list_del(node *head){
	node * p1 = head;
	node * p2;
	while(p1 != NULL){
		p2 = p1;
		p1 = p1 -> next;
		free(p2);
	}
}
//修改指定节点的数据（头节点为0号），反回修改的节点的指针
node * node_modify(node *head, int i, int data){
	node *p = head;
	while(i > 0){
		if(p -> next == NULL)return NULL;
		p = p -> next;
		i--;
	}
	p -> data = data;
	return p;
}
```
