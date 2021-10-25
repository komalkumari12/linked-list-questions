# linked-list-questions
#include<stdlib.h>
#include <stdio.h>

struct node{
    int data ;
    struct node* next ;
};

struct node*addFirstNode(int data){
    struct node *new=(struct node*)malloc(sizeof(struct node)) ;
    new->data= data ;
    new->next =NULL ;
    
    return new ;
}

struct node*addAtLast(struct node*head ,int data)
{
    struct node *new=(struct node*)malloc(sizeof(struct node)) ;
    new->data=data ;
    new->next =NULL ;
    
    struct node*temp ;
    temp=head ;
    
    while(temp->next!=NULL)
    {
        temp=temp->next ;
    }
    
    temp->next=new ;
    
    head=temp ;
    
    return head ;
}

struct node* createlist (struct node*head)
{
    int i, n,data ;
    
    printf("enter number of nodes to be inserted: ") ;
    scanf("%d", &n ) ;
    
    if(n==0){
        printf("list is empty \n") ;
        exit(1) ;
    }
    
    printf("enter data of first node :") ;
    scanf("%d", &data) ;
    head=addFirstNode(data) ;
    
    for(i=1; i<n ;i++){
        printf("enter data of %d node :",i+1) ;
        scanf("%d", &data) ;
        addAtLast(head,data) ;
    }
    
    return head ;
}

void printAllElements(struct node*head){
    struct node*temp=NULL ;
    temp =head ;
    
    while(temp!=NULL)
    {
        printf("%d ",temp->data) ;
        temp=temp->next;
    }
}

stuct node* delFirstnode(struct node*head){
    stuct node* temp=NULL ;
    temp=head ;
    
    head=head->next ;
    free(temp) ;
    temp=NULL ;
    
    return head ;
}

struct node* delLastNode(struct node){
    stuct node* prev=NULL ,*current=NULL;
    current=head ;
    
    while(current!=NULL){
        current=current->next ;
        prev=current ;
    }
    
    free(prev) ;
    prev=NULL ;
    
    return head ;
}

struct node* delFromPos(struct node* head,int pos){
      stuct node* prev=NULL ,*current=NULL;
    current=head ;
    
    while(pos>1){
        current=current->next ;
        prev=current ;
    }
    
    prev->next=current->next ;
    free(current) ;
    current=NULL ;
}

int main()
{
    struct node* head ;
    head=NULL ;
    
    head=createlist(head) ;
    
    //printf("%d ",head->data);
    printAllElements(head) ;

    return 0;
}
