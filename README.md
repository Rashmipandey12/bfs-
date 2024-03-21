# bfs-
bfs
typedef struct node{
  int visit[mx];
  int matrix[mx][mx];
  int num;
}Graph;
void init(Graph*graph,int num){
  graph->num=num;
  for(int i=0;i<num;i++){
    for(int j=0;j<num;j++){
      graph->matrix[i][j]=0;
    }
    
  }
}
void addedge(Graph*graph,int u,int v){
  graph->matrix[u][v]=1;
  graph->matrix[v][u]=1;
}
void display(Graph *graph){
  for(int i=0;i<graph->num;i++){
    for(int j=0;j<graph->num;j++){
      printf("%d",graph->matrix[i][j]);
    }
  }
}
void bfs(Graph*grap,int node){
  bool visited[mx];
  for(int i=0;i<graph->num;i++){
    visited[i]=false;
  }
  int queue[mx];
  int front=0;
  int rear=0;
  visited[node]=true;
  queue[rear++]=node;
  while(front!=rear){
    node=queue[front++];
    printf("%d",node);
    for(int i=0;i<graph->num;i++){
      if(graph->matrix[node][i]&&!visited[i]){
        visited[i]=true;
        queue[rear++]=i;
      }
    }
  }
} 
void main(){
  int var;
  Graph graph;
  init(&graph,5);
  addedge(&graph,0,1);
  addedge(&graph,0,3);
   addedge(&graph,2,4);
   addedge(&graph,0,2);
  while(1){
    printf("1.print the adj matrix,2.bfs 3.exit");
    printf("enter your chouice");
    scanf("%d",&var);
    switch(var){
      case 1:display(&graph);
      break;
      case 2:bfs(&graph,0);
        break;
      case 3:exit(0);
      printf("\n");
      break;
    }
  }
}
