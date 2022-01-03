#include<stdio.h>
#include<stdlib.h>
struct double_linked_list
{
    int data;
    struct double_linked_list *left,*right;
};
typedef struct double_linked_list node;
node *create(node *first)
{
    node *new,*prev;
    int x;
    printf("enter the data into double linked list(enter -1 to stop)");
    scanf("%d",&x);
    while(x!=-1)
    {
        new=(node*)malloc(sizeof(node));
        new->data=x;
        new->left=NULL;
        new->right=NULL;
        if(first==NULL)
        {
            first=new;
            prev=new;
        }
        else
        {
            prev->right=new;
            new->left=prev;
            prev=new;
        }
        printf("enter the data into double linked list(enter -1 to stop)");
        scanf("%d",&x);
    }
    return first;
}
void display(node *first)
{
    node *temp=first;
    if(first==NULL)
    {
        printf("No list to display");
    }
    else
    {
        while(temp!=NULL)
        {
            printf("<- |%d|-> ",temp->data);
            temp=temp->right;
        }
        printf("NULL");
    }
}
int count(node *first)
{
    node *temp=first;
    int c=0;
    while(temp!=NULL)
    {
        c++;
        temp=temp->right;
    }
    return c++;
}
void search(node *first,int x)
{
    node *temp=first;
    int flag=0;
    while(temp!=NULL)
    {
        if (temp->data==x)
        {
            flag=1;
            break;
        }
        temp=temp->right;
    }
    if(flag==1)
    {
        printf("%d element is found\n",x);
    }
    else
    {
        printf("%d element is not found\n",x);
    }
}
node *insert_at_begin(node *first,int x)
{
    node *new;
    new=(node*)malloc(sizeof(node));
    new->data=x;
    new->right=NULL;
    new->left=NULL;
    if(first==NULL)
    {
        first=new;
    }
    else
    {
        new->right=first;
        first->left=new;
        first=new;
    }
    return first;
}
node *insert_at_end(node *first,int x)
{
    node *temp=first,*new;
    new=(node *)malloc(sizeof(node));
    new->data=x;
    new->right=NULL;
    new->left=NULL;
    if(first==NULL)
    {
        first=new;
    }
    else
    {
        while(temp->right!=NULL)
        {
            temp=temp->right;
        }
        temp->right=new;
        new->left=temp;
        new->right=NULL;
    }
    return first;
}
node *insert_at_Pos(node *first,int x, int pos)
{
    node *new,*temp=first;
    int n;
    new=(node *)malloc(sizeof(node));
    new->data=x;
    new->right=NULL;
    new->left=NULL;
    if(pos>1&&pos<n)
    {
        for(int i=1;i<pos-1;i++)
        {
            temp=temp->right;
        }
        new->right=temp->right;
        new->left=temp;
        temp->right=new;
        new->right->left=new;
    }
    return first;
}
node* begin_delete(node *first)
{
        node *temp=first;
        first=temp->right;
        free(temp);
        return first;
}
node* random_delete(node *first,int pos)
{
        int i;
        node *temp=first;
        node *temp1;
        for (i=1;i<pos;i++)
        {
                temp1=temp;
                temp=temp->right;
        }
        temp->right->left=temp1;
        temp1->right=temp->right;
        free(temp);
        return first;
}
void main()
{
    node *head=NULL;
    int ch,pos,c,x,i;
    printf("Menu Driven\n1.Create\n2.Display\n3.Count\n4.Search\n5.Insert at beginning\n6.Insert at ending\n7.Insert at given position\n8.Delete\n9.Random Delete\n10.Exit\n");
    while(1)
    {
        printf("Enter your choice\n");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1:head=create(head);
                   break;
            case 2:display(head);
                   break;
            case 3:c=count(head);
                   printf("Number of nodes is %d\n",c);
                   break;
            case 4:printf("enter x:");
                   scanf("%d",&x);
                   search(head,x);
                   break;
            case 5:printf("enter x:");
                   scanf("%d",&x);
                   head=insert_at_begin(head,x);
                   break;
            case 6:printf("enter x: ");
                   scanf("%d",&x);
                   head=insert_at_end(head,x);
                   break;
            case 7:printf("enter x,pos: ");
                   scanf("%d %d",&x,&pos);
                   head=insert_at_Pos(head,x,pos);
                   break;
            case 8:head=begin_delete(head);
                   break;
            case 9:printf("Enter the position: ");
                   scanf("%d",&pos);
                   head=random_delete(head,pos);
                   break;
            case 10:exit(0);
                   break;
            default:printf("enter the correct choice\n");
                    break;
        }
    }
}
Output
menu driven

1.create

2.display

3.count

4.search

5.insert at beginning

6.insert at ending

7.insert at given position

8.delete

9.random delete

10.exit

enter your choice

1

enter the data into double linked list(enter -1 to stop)9

enter the data into double linked list(enter -1 to stop)7

enter the data into double linked list(enter -1 to stop)6

enter the data into double linked list(enter -1 to stop)4

enter the data into double linked list(enter -1 to stop)-1

enter your choice

2

<- |9|-> <- |7|-> <- |6|-> <- |4|-> nullenter your choice

3

number of nodes is 4

enter your choice

4

enter x:6

6 element is found

enter your choice

5

enter x:2

enter your choice

2

<- |2|-> <- |9|-> <- |7|-> <- |6|-> <- |4|-> nullenter your choice

6

enter x: 73      3

enter your choice

2

<- |2|-> <- |9|-> <- |7|-> <- |6|-> <- |4|-> <- |3|-> nullenter your choice

7

enter x,pos: 4

1

enter your choice

8   2

<- |2|-> <- |9|-> <- |7|-> <- |6|-> <- |4|-> <- |3|-> nullenter your choice

8

enter your choice

2

<- |9|-> <- |7|-> <- |6|-> <- |4|-> <- |3|-> nullenter your choice

9

enter the position: 5
