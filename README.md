#include<pthread.h>
#include<stdlib.h>
#include<stdio.h>
#include<unistd.h>

int Fibonacci(int n)
{
	if(n==0||n==1)
	return n;
	else
	 return (Fibonacci(n-1)+Fibonacci(n-2));
}
void* fibonacci_thread(void* var)
{	
	sleep(1);
	int *i=(int *)var;
	printf("Calculating fibonacci");
	for(int j=1;j<=*i;j++)
	 printf("%d ",Fibonacci(j));
	 return NULL;
	 
}
int  main()
{
	int n;
	pthread_t bck;
	printf("Enter the number to show fibonacci series:");
	scanf("%d",&n);	
	pthread_create(&bck,NULL,fibonacci_thread,(void*)n);
	pthread_join(bck,NULL);
	pthread_exit(NULL);
}
