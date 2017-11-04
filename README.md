# Prim

Prim

#include <iostream>
  
using namespace std;

#define M 2001

int set[M]={0},g[M][M];

char str[M][8];

inline void make_map(int n,int g[M][M]){

	int i,j,k;
  
  
	for(i=1;i<=n;i++){
  
		for(j=i+1;j<=n;j++){
    
			int c=0;
      
			for(k=0;k<7;k++)
      
				if(str[i][k]!=str[j][k]) c++;
        
			g[i][j]=g[j][i]=c;
      
		}
    
	}
  
}


int main(){

	int n,q[M],qf=0,ql=0,d[M],u;
  
	char c;
  
	scanf("%d%c",&n,&c);
  
	int i;
  
	while(n!=0){
  
		memset(set,0,sizeof(set)); memset(g,0,sizeof(g));
    
		for(i=1;i<=n;i++) {
    
			scanf("%s",&str[i]);
      
			q[i-1]=i;
      
			d[i]=2000000;
      
		}
    
		qf=0;ql=n-1;
    
		make_map(n,g);
    
		int sum=0;
    
		int f=false;
    
		while(qf<=ql){
    
			int min=qf;
      
			for(i=qf+1;i<=ql;i++){
      
				if(d[q[i]] < d[q[min]]) min=i;
        
			}
      
			swap(q[qf],q[min]);
      
			u=q[qf]; qf++;
      
			if(f) sum+=d[u];
      
			for(i=1;i<=n;i++){
      
				if(g[u][i] !=0 && g[u][i] < d[i]) d[i]=g[u][i];
        
			}
      
	f=true;
  
		}
    
		printf("The highest possible quality is 1/%d.\n",sum);
    
		scanf("%d%c",&n,&c);
    
	}
  
	return 0;
  
}

