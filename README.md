# dfs









[5:24 pm, 05/05/2023] Akshay Pawar: #include<stdio.h>
#define SIZE 10
/* Stack Data Structure */
#define BOTTOM -1
#define S_SIZE 100
int stack[S_SIZE];
int top;
/* Graph Data Structure */
int G[SIZE][SIZE]; // To store Graph
int nov; // To store no. of Vertices
int noe; // To store no. of edges
int visited[SIZE];
/* Stack Code */
void init_stack()
{
top = BOTTOM;
}
int isFull()
{
if(top == S_SIZE - 1)
return 1;
else
return 0;
}
[5:24 pm, 05/05/2023] Akshay Pawar: int isEmpty()
{
if(top == BOTTOM)
return 1;
else
return 0;
}
void push(int item)
{
if(isFull())
{
printf("Stack is Full !! \n");
}
else
{
top++;
stack[top] = item;
}
}
int pop()
{
int item;
if( isEmpty())
{
return -1;
}
else
{
item = stack[top];
top--;
return item;
}
}
[5:25 pm, 05/05/2023] Akshay Pawar: int peek()
{
if( isEmpty())
{
return -1;
}
else
{
return stack[top];
}
}
void accept()
{
int i,j,k;
printf("How many Vertices : ");
scanf("%d", &nov);
printf("How many Edges : ");
scanf("%d", &noe);
for(k=1; k<=noe; k++)
{
printf("Enter Edge (Vi,Vj) : ");
scanf("%d %d", &i,&j);
G[i][j] = 1;
G[j][i] = 1; //remove this line in case of directed Graph
}
}
[5:25 pm, 05/05/2023] Akshay Pawar: void display()
{
int i,j;
printf("\nAdjacency Matrix\n");
printf("------------------\n");
for(i=0; i<nov; i++)
{
for(j=0; j<nov; j++)
{
printf("%d ", G[i][j]);
}
printf("\n");
}
}
void dfs(int start)
{
int i,j,status;
printf("\nDFS [Start V%d] : ", start);
printf("%d ", start);
visited[start] = 1;
push(start);
while(!isEmpty())
{
i = peek();
status = 0;
for( j=0; j<nov; j++)
{
if(G[i][j] == 1 && visited[j]==0)
{
printf("%d ", j);
visited[j] = 1;
push(j);
status = 1;
[5:25 pm, 05/05/2023] Akshay Pawar: break;
}
}
if(status == 0)
{
pop();
}
}
printf("\n");
}
int main()
{
int start;
accept();
display();
init_stack();
printf("\nEnter Starting Vertex : ");
scanf("%d", &start);
dfs(start);
}
OUTPUT
How many Vertices : 7
How many Edges : 10
Enter Edge (Vi,Vj) : 0 3
Enter Edge (Vi,Vj) : 0 1
Enter Edge (Vi,Vj) : 0 5
Enter Edge (Vi,Vj) : 3 1
Enter Edge (Vi,Vj) : 5 1
Enter Edge (Vi,Vj) : 1 4
Enter Edge (Vi,Vj) : 1 2
Enter Edge (Vi,Vj) : 1 6
Enter Edge (Vi,Vj) : 4 2
Enter Edge (Vi,Vj) : 6 2
