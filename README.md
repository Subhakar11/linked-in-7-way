#include<stdio.h>
#include<stdlib.h>

struct node{
int data;
struct node *link;
};

void print(struct node *ptr){
while(ptr!=NULL){

printf("Element is : %d\n  ",ptr->data);
ptr=ptr->link;
}
}
struct node * insertAtFirst(struct node * head, int data) {
struct node * ptr = (struct node *) malloc(sizeof(struct node));
ptr->link = head;
ptr->data = data;
return ptr;
}

struct node * insertAtindex(struct node * head , int data , int index){
struct node * ptr;
ptr = (struct node *) malloc(sizeof(struct node));
struct node *p = head;
int i=0;
while (i!=index-1){
p=p->link;
i++;
}
ptr->data = data;
ptr->link = p->link;
p->link = ptr;
return head;
}
struct node* InsertAtEnd(struct node *head, int data){
struct node* ptr = (  struct node*)malloc(sizeof(struct node));
ptr->data= data;
struct node *p = head;
while(p->link != NULL){
p=p->link;
}
p->link=ptr;
ptr->link = NULL;
return head;
}
struct node* InsertAtnode(struct node *head,struct node *prenode ,int data){
struct node *ptr = (struct node*)malloc(sizeof(struct node));
ptr->data = data;
ptr->link=prenode->link;
prenode->link = ptr;
return head;
}

struct node *  DeletAtfirst(struct node *head){
    struct node *ptr;
   
    ptr=head;
    head = head->link;
    free(ptr);
    return head;
}
struct node * DeletAtindex(struct node*head,int index){

   struct node *p = head;
   struct node *q = head->link;
    for(int i=0;i<index-1;i++){
    p=p->link;
    q=q->link;
}
p->link = q->link;

     free(q);
return head;
 }
    struct node* DeletAtlast(struct node * head){
     struct node *p = head;
   struct node *q = head->link;
    while(q->link  != NULL){
    p=p->link;
    q=q->link;
}
p->link = NULL;
free(q);
     return head;
   }
   struct node * DeletAtvalue(struct node *head , int value){
struct node *p = head;
   struct node *q = head->link;
    while( q->data!=value && q->link!=NULL){
    p=p->link;
    q=q->link;
}
if(q->data==value)
{
p->link=q->link;

}
free(q);
return head;
 }

int main(){
int n;
struct node *head, *head1 ,*head2,*head3;
head = (struct node*)malloc(sizeof(struct node));
head1= (struct node*)malloc(sizeof(struct node));
head2 = (struct node*)malloc(sizeof(struct node));
head3 = (struct node*)malloc(sizeof(struct node));

head->data=11;
head->link= head1;

head1->data=22;
head1->link= head2;

head2->data=33;
head2->link= head3;

    head3->data=44;
head3->link= NULL;

print(head);

printf("\n\nFor Insertion press :\n\n");
printf("  1 Insert At First \n");
printf(" 2 Insert At Index \n");
printf(" 3 Insert At End \n ");
printf(" 4 Insert At Node \n");
printf("\nFor deletion press :\n\n");
printf(" 5 Delet At frist\n");
printf("6 Delet At index\n");
printf("7 Delet At End\n");
printf("8 Delet At any value\n");

scanf("%d",&n);
switch(n){

case 1:

printf("Enter the element for first:\n");
int m;
scanf("%d",&m);
printf("Inserted value is:\n");
head =  insertAtFirst(head,m);
print(head);

break;

case 2:

printf("Enter Index:");
int l;
scanf("%d",l);
printf("Enter element:\n");
int k;
scanf("%d",k);
printf("Inserted value is:\n");
head =  insertAtindex(head, 2,123);
print(head);
break;
case 3:

printf("Enter element:");
int p;
scanf("%d",&p);
printf("Inserted value is:\n");
head = InsertAtEnd(head,p);
print(head);
break;

case 4:

printf("These are node head , head1 , head2, head3  \n");
char N[10];
printf("Enter any node:\n");
scanf("%s",N);
printf("Enter element:\n");
int s;
scanf("%d",&s);
printf("Inserted value is:\n");
head = InsertAtnode(head,N,s);
print(head);
break;

case 5:

head = DeletAtfirst(head);
       printf("After deletion :\n");
       print(head);
 break;

case 6:

printf("Enter the index :\n");
int a;
scanf("%d",&a);

printf("After deletion :\n");
     
 head = DeletAtindex(head, a);
 print(head);
break;

 case 7:

  printf("After deletion :\n");
head =DeletAtlast(head);
print(head);
break;

case 8:

printf("Enter the value:\n");
int d;
scanf("%d",&d);
printf("After deletion :\n");
head = DeletAtvalue(head,d);

print(head);
break;
default:
printf("wrong responce\n");
break;

}

return 0;
}


