#include <stdio.h> 
#include <stdlib.h>
#include <string.h>



typedef struct node{ 
     int data;
     struct node *left,*right;
}node;



node* new_node(int data)
{
    struct node *p;
    p = malloc(sizeof(struct node));
    p->data = data;
    p->left = NULL;
    p->right = NULL;

    return(p);
}

node *tree1(){
	
	node *root = new_node(12);
	root->left = new_node(9);
	root->right = new_node(8);
	
	return(root);
	
}
node *tree2(){
	
	node *root = new_node(12);
	root->left = new_node(9);
	root->left->right = new_node(5);
	root->left->right->left = new_node(7);
	
	return(root);
}
node *tree3(){
	
	node *root = new_node(12);
	root->left = new_node(9);
	root->right = new_node(8);
	root->left->left = new_node(1);
	root->left->right = new_node(5);
	root->right->right = new_node(4);
	root->right->right->left = new_node(7);
	root->right->right->right = new_node(6);
	
	return(root);
}

void prefix(node *root){
    if(root!=NULL)
    {
        printf(" %d ", root->data);
        prefix(root->left);
        prefix(root->right);
    }}

void postfix(struct node *root){
    if(root!=NULL)
    {
        postfix(root->left);
        postfix(root->right);
        printf(" %d ", root->data);
    }}

void infix(node *root){
    if(root!=NULL)
    {
        infix(root->left);
        printf(" %d ", root->data);
        infix(root->right);
    }}
int size(node *head)  
{   
  if (head==NULL)  
    return 0; 
  else     
    return(size(head->left) + 1 + size(head->right));   
} 
int somtree(node *head) 
{ 
    if (head == NULL) 
        return 0; 
    return (head->data + somtree(head->left) + somtree(head->right)); 
} 
int longur(node *head)  
{ 
   if (head==NULL)  
       return (0);
    else if(head->left==NULL && head->right==NULL)  
       return (0); 
   else 
   { 
 
       int l = 1+longur(head->left); 
       int r = 1+longur(head->right); 
  
       if (l > r)  
           return(l); 
       else return(r); 
   } 
}  


int main(){
	int a;

	here2:
		
	printf("  TREE : 1\n     12\n    /  %c\n   9    8\n",92);
	printf("\n  TREE : 2\n     12\n    /\n   9\n    %c\n     5\n    /\n   7\n",92);
	printf("\n  TREE : 3\n     12\n    /  %c\n   9    8\n  / %c    %c\n 1   5    4\n         / %c\n        7   6\n",92,92,92,92);
	printf("\nplease select which tree to present : ");
	
		scanf("%d",&a);
	
	switch (a){
		
		case 1:
			printf("  TREE : 1\n     12\n    /  %c\n   9    8\n",92);
			
			printf("\n\nprefix\n\n");

				prefix(tree1());
				
			printf("\ninfix\n\n");
	
				infix(tree1());
				
			printf("\npostfix\n\n");
	
				postfix(tree1());
				
			printf("\n\nnumber of nodes = %d\n",size(tree1()));
			
			printf("\nsome de nodes = %d\n",somtree(tree1()));
			
			printf("\nhauter of tree = %d\n",longur(tree1()));
			
			break;
		
		case 2:
			printf("\n  TREE : 2\n     12\n    /\n   9\n    %c\n     5\n    /\n   7\n",92);
			
			printf("\n\nprefix\n\n");

				prefix(tree2());
				
			printf("\ninfix\n\n");
	
				infix(tree2());
				
			printf("\npostfix\n\n");
	
				postfix(tree2());
				
			printf("\n\nnumber of nodes = %d\n",size(tree2()));
			
			printf("\nsome de nodes = %d\n",somtree(tree2()));
			
			printf("\nhauter of tree = %d\n",longur(tree2()));
			
			break;
			
		case 3:
			printf("\n  TREE : 3\n     12\n    /  %c\n   9    8\n  / %c    %c\n 1   5    4\n         / %c\n        7   6\n",92,92,92,92);
			
			printf("\n\nprefix\n\n");

				prefix(tree3());
				
			printf("\ninfix\n\n");
	
				infix(tree3());
			
			printf("\npostfix\n\n");
	
				postfix(tree3());
				
			printf("\n\nnumber of nodes = %d\n",size(tree3()));
			
			printf("\nsome de nodes = %d\n",somtree(tree3()));
			
			printf("\nhauter of tree = %d\n",longur(tree3()));
			
			break;
			
		default :
			printf("\nERROR #: 898\n\npress any key to continue :\n\n");
			goto here2;
		
	}
	
		
	
	return (0);

}










