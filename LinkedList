#include <stdio.h>
#include <string.h>
#include <stdlib.h>

//structure
typedef struct ListNode{
	char data[20];
	struct ListNode *link;
}listNode;

typedef struct{
	listNode * head;
	listNode * tail;
}linkedList_h;

//function def
void printList(linkedList_h*);
void insertFirstNode();
void insertLastNode();
linkedList_h* createLinkedList_h();
void freeLinkedList_h(linkedList_h *);
listNode* searchNode(linkedList_h *, char*);
void insertMiddleNode();
void deleteNode();
void deleteFirstNode();
void deleteLastNode();
void reverse();
void reverse_a();

//main
void main()
{
	linkedList_h * L;
	L=createLinkedList_h();
	printf("[empty list created.]\n");
	printList(L);
	printf("\n");

	printf("[(F)insert into List.]\n");
	insertFirstNode(L, "Jeon");
	printList(L);
	printf("\n");

	printf("[(F)insert into List.]\n");
	insertFirstNode(L, "I'm");
	printList(L);
	printf("\n");

	printf("[(F)insert into List.]\n");
	insertFirstNode(L, "Hi!");
	printList(L);
	printf("\n");

	printf("[(L)insert into List.]\n");
	insertLastNode(L, "yun");
	printList(L);
	printf("\n");

	printf("[(L)insert into List.]\n");
	insertLastNode(L, "hye");
	printList(L);
	printf("\n");

	listNode* p;
	printf("[search Hi!]\n");
	p=searchNode(L, "Hi!");
	if(p==NULL) printf("No data\n");
	else printf("data : %s\n\n", p->data);

	printf("[insert Hello! between Hi! and I'm]\n");
	insertMiddleNode(L, p, "Hello!");
	printList(L);
	printf("\n");

	printf("reverse print\n");
	reverse(L);
	printList(L);
	printf("\n");
	
	printf("REA\n");
	reverse_a(L->head);
	printf("\n\n");	

	printf("[delete Hi!]\n");
	p=searchNode(L, "Hi!");
	deleteNode(L, p);
	printList(L);
	printf("\n");

	printf("[First Del]\n");
	deleteFirstNode(L);
	printList(L);
	printf("\n");

	printf("[Last Del]\n");
	deleteLastNode(L);
	printList(L);
	printf("\n");

	printf("[free]\n");
	freeLinkedList_h(L);
	printList(L);
	printf("\n");

}

//function
linkedList_h * createLinkedList_h(void)
{
	linkedList_h* L;
	L=(linkedList_h*)malloc(sizeof(linkedList_h));
	L->head=NULL;
	L->tail=NULL;
	return L;
}

void freeLinkedList_h(linkedList_h * L)
{
	listNode * p;
	while(L->head!=NULL)
	{
		p=L->head;
		L->head=L->head->link;
		free(p);
		p=NULL;
	}
}

void printList(linkedList_h * L)
{

	if(L->head == NULL){
		printf("list is empty\n");
	}else{		
		listNode * p;
		p=L->head;
		
		while(p->link != NULL)
		{
			printf("%s >>  ", p->data);
			p = p->link;
		}
		printf("%s\n", p->data);
	}
}

void insertFirstNode(linkedList_h * L, char *data)
{
	
	listNode* newNode = (listNode*)malloc(sizeof(listNode));
	strcpy(newNode->data, data);

	if(L->head == NULL){
		newNode->link = NULL;
		L->head = newNode;
	}else{
		newNode->link = L->head;
		L->head = newNode;
	}
}

void insertLastNode(linkedList_h * L, char *data)
{
	listNode * p;
	p=L->head;

	listNode* newNode=(listNode*)malloc(sizeof(listNode));
	strcpy(newNode->data, data);

	while(1)
	{
		if(p->link==NULL)
		{
			newNode->link=NULL;
			p->link=newNode;
			break;
		}
		p=p->link;

	}
}

listNode * searchNode(linkedList_h * L, char * data)
{
	listNode * p;

	p=L->head;

	while(p!=NULL)
	{
		if(strcmp(p->data, data)==0) return p;
		else p=p->link;
	}

	return p;
}

void insertMiddleNode(linkedList_h * L, listNode * n, char * data)
{
	listNode * newNode=(listNode*)malloc(sizeof(listNode));
	strcpy(newNode->data, data);

	newNode->link=n->link;
	n->link=newNode;
}

void deleteNode(linkedList_h * L, listNode* n)
{
	if(L->head==NULL) printf("empty\n");
	else
	{
		listNode * p;
		p=L->head;

		while(1) 
		{
			//if(0==strcmp(p->link->data,n->data))
			if(L->head==n)
			{
				L->head=n->link;
				free(n);
				break;
			}
			if(p->link==n){
				p->link=n->link;
				free(n);
				break;
			}
			p=p->link;
		}
	}
}

void deleteFirstNode(linkedList_h * L)
{
	listNode * p;
	p=L->head;

	if(L->head==NULL) printf("empty\n");
	else
	{
		L->head=p->link;
		free(p);
	}
}

void deleteLastNode(linkedList_h * L)
{
	listNode * p;
	p=L->head;

	if(L==NULL) printf("empty\n");
	else
	{
		while(1)
		{
			if(p->link->link==NULL)
			{
				p->link=NULL;
				free(p->link);
				break;	
			}
			p=p->link;
		}

	}
}

void reverse(linkedList_h *L)
{
	listNode *p;
	p=L->head;

	if(p!=NULL)
	{
		listNode *cur = L->head;
		listNode *nxt=cur->link;
		listNode *tmp=nxt->link;
		L->tail=cur;
		L->tail->link=NULL;

		for(;;)
		{

			nxt->link=cur;
			if(tmp==NULL) break;
			cur=nxt;
			nxt=tmp;
			tmp=tmp->link;
		}
		L->head=nxt;
	}

}

void reverse_a(listNode * h)
{
	if(h->link){
		reverse_a(h->link);
	}
	printf("%s  ", h->data);
}
