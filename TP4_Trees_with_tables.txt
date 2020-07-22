#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int nb = 0;



void sign ()
{

  printf ("**************************************************\n");
  printf ("*                                                *\n");
  printf ("*            Hadjazi Mohammed Hisham             *\n");
  printf ("*                                                *\n");
  printf ("*     Group_05 TP_04_Part_1+2 Trees_solution     *\n");
  printf ("*                                                *\n");
  printf ("**************************************************\n");
  printf ("\n\n\n");
}






void new_tree (char *tab)
{
  int i;
  for (i = 1; i <= 10000; i++)
    {
      tab[i] = '\0';
    }
  printf ("\nJOB DONE =)");
}

int find (char c, char *tab)
{
  int i = 0;
  for (i = 1; i <= 10000; i++)
    {
      if (tab[i] == c)
	return i;
    }



  return 99999;
}

void new_node (int nb, char *tab)
{
  char c;
  printf ("\nnew value = ");
  scanf (" %c", &c);
  if (nb == 0)
    {
      tab[nb + 1] = c;
      printf ("\n%c is the root of the tree.", tab[nb]);
    }
  else
    {
      tab[nb + 1] = c;
      printf ("\n%c is now is entered and now at the end of the tree =)",
	      tab[nb + 1]);
    }
}

void do_fg (char *tab)
{

  char c, d;
  int i = 0;
  printf ("\nplease enter value of racine = ");
  scanf (" %c", &d);
  i = find (d, tab);
  //printf("%d",i);
  if (i == 99999)
    printf ("\nsorry value not found =(");
  else
    {
      if (tab[i * 2] == '\0')
	nb++;
      printf ("\nnew value = ");
      scanf (" %c", &c);
      tab[i * 2] = c;
      printf ("\n%c is now is FG of %c =)", tab[i * 2], tab[i]);
    }
}

void do_fd (char *tab)
{

  char c, d;
  int i = 0;
  printf ("\nplease enter value of racine = ");
  scanf (" %c", &d);
  i = find (d, tab);
  if (i == 99999)
    printf ("\nsorry value not found =(");
  else
    {
      if (tab[i * 2 + 1] == '\0')
	nb++;
      printf ("\nnew value = ");
      scanf (" %c", &c);
      tab[i * 2 + 1] = c;
      printf ("\n%c is now is FD of %c =)", tab[i * 2 + 1], tab[i]);
    }
}

void do_racine (char *tab)
{


  char c, d;
  int i = 0;
  printf ("\nplease enter value of node = ");
  scanf (" %c", &d);
  i = find (d, tab);
  if (i == 99999)
    printf ("sorry value not found =(");
  else
    {
      printf ("\nnew value = ");
      scanf (" %c", &c);
      tab[i / 2] = c;
      printf ("\n%c is now is racine of %c =)", tab[i / 2], tab[i]);

    }
}




int fdd (int i, char *tree)
{
  if (tree[i] != '\0' && ((2 * i) + 1) <= 10000)
    return (2 * i) + 1;
  return -1;
}



int fgg (int i, char *tree)
{
  if (tree[i] != '\0' && (2 * i) <= 10000)
    return 2 * i;
  return -1;
}

void fd (char *tree)
{
  char d;
  int i = 0;
  printf
    ("\nplease enter the the value you are looking for his right child = ");
  scanf (" %c", &d);
  i = find (d, tree);
  if (i == 99999)
    printf ("\nsorry value not found =(");
  else
    {
      if (tree[i * 2 + 1] == '\0')
	printf ("\nsorry no fice droit =(");
      else
	printf ("\n%c is fice droit of %c", tree[i * 2 + 1], tree[i]);

    }
}



void fg (char *tree)
{

  char d;
  int i = 0;

  printf
    ("\nplease enter the the value you are looking for his left child = ");
  scanf (" %c", &d);

  i = find (d, tree);

  if (i == 99999)
    printf ("\nsorry value not found");
  else
    {
      if (tree[i * 2] == '\0')
	printf ("\nsorry no fice droit");
      else
	printf ("\n%c is fice gouch of %c", tree[i * 2], tree[i]);

    }
}

void pere (char *tree)
{

  char d;
  int i = 0;

  printf ("\nenter value of child = ");
  scanf (" %c", &d);

  i = find (d, tree);

  if (i == 99999)
    printf ("\nsorry value not found =(");
  else
    {
      if (i == 1)
	printf ("\nsorry this is the root, it has no root =)");
      else
	printf ("\n%c is pere %c", tree[i / 2], tree[i]);

    }
}

void preorder (int i, char *tree)
{
  if (index > 0 && tree[i] != '\0')
    {
      printf (" %c ,", tree[i]);
      preorder (fgg (i, tree), tree);
      preorder (fdd (i, tree), tree);
    }
}



void postorder (int i, char *tree)
{
  if (i > 0 && tree[i] != '\0')
    {
      postorder (fgg (i, tree), tree);
      postorder (fdd (i, tree), tree);
      printf (" %c ,", tree[i]);
    }
}



void inorder (int i, char *tree)
{
  if (i > 0 && tree[i] != '\0')
    {
      inorder (fgg (i, tree), tree);
      printf (" %c ,", tree[i]);
      inorder (fdd (i, tree), tree);
    }
}

void insert(int num,int loc,char *tree)
{
	int par;
	while(loc>0)
	{
		par=(loc)/2;
		if(num<=tree[par])
		{
			tree[loc]=num;
			return;
		}
		tree[loc]=tree[par];
		loc=par;
	}
	tree[1]=num;
}

void draw (char *tree)
{

  printf ("\nnumber of nodes = %d",nb);
  printf ("\ninorder :\n");
  inorder (1, tree);
  printf ("\npostorder :\n");
  postorder (1, tree);
  printf ("\npreorder :\n");
  preorder (1, tree);
  


}

void printtable (char *tree)
{

  int i = 0;
  for (i = 0; i <= 10000; i++)
    {
      if (tree[i] != '\0')
	printf ("%c\n", tree[i]);

    }
}

void racine (char *tree)
{

  int i = 1;
  printf ("\nracine de arbres = %c at index %d", tree[i], i);
}

void val (char *tree)
{
	int i=0;
	
	printf("\nplease enter an index to know its value : ");
	scanf (" %d", &i);
		
		if ( i == 0 || i > nb )
			printf("\nsorry out of range =(");
			
		else if ( tree[i] == '\0')
			printf("\nnode is empty =)");
			
		else
			printf("\nvaluer of index %d = %c",i,tree[i]);
}


void vide (char *tree)
{

	if ( tree[1] == '\n')
		printf("\ntree is emptry =)");
		
	else
		printf("\n nope tree is not empty =)");



}


void del (char *tree)
{
	int left,right,i,temp,par;
	char d;
	 
	 printf("\nplease enter node you want to delete = ");
	 scanf (" %c", &d);

		i = find (d, tree);

		if (i == 99999){
			printf ("\nsorry value not found");
			return;
		}
		else
    {

	tree[i]=tree[nb];
	tree[nb]='\0';
	nb=nb-1;
	par=(i)/2;
	if(tree[i] > tree[par])
	{
		insert( tree[i],i,tree);
		return;
	}
	left=2*i;
	right=2*i+1;
	while(right < nb)
	{
		if( tree[i]>=tree[left] && tree[i]>=tree[right] )
			return;
		if( tree[right]<=tree[left] )
		{
			temp=tree[i];
			tree[i]=tree[left];
			tree[left]=temp;
			i=left;
		}
		else
		{
			temp=tree[i];
			tree[i]=tree[right];
			tree[right]=temp;
			i=right;
		}
		left=2*i;
		right=2*i+1;
	}
	if( left==nb && tree[i]<tree[left] )
	{	temp=tree[i];
		tree[i]=tree[left];
		tree[left]=temp;
	}
}

}





int main ()
{

  int a;
  char tree[10000];

  sign ();

here:
  printf
    ("\n\nActions available : \n1: creer arbre vide.\t2: creer sommet.\n3: faire_FG. \t\t4: Fair_FD.\n5: Faire_racine.\t6: Suprimer feuille.\n7: Racine ?\t\t8: fils_gouche.\n9: fils_droit.\t\t10: Pere ?.\n11: Valluer ?.\t\t12: est_vide ?.\n13: Show the list.\t0: exit the program.\n");
  printf ("\n\nplease select action = ");
  scanf ("%d", &a);

  switch (a)
    {

    case 0:
      break;
    case 1:
      new_tree (tree);
      nb = 0;
      goto here;
    case 2:
      new_node (nb, tree);
      nb = nb + 1;
      goto here;
    case 3:
      do_fg (tree);
      goto here;
    case 4:
      do_fd (tree);
      goto here;
    case 5:
      do_racine (tree);
      goto here;
    case 6:
      del(tree);
      goto here;
    case 7:
      racine (tree);
      goto here;
    case 8:
      fg (tree);
      goto here;
    case 9:
      fd (tree);
      goto here;
    case 10:
      pere (tree);
      goto here;
    case 11:
      val(tree);
      goto here;
    case 12:
      vide(tree);
      goto here;
    case 13:
      draw (tree);
      //printtable(tree);
      goto here;

    default:
      goto here;
    }




}
