Student Name: Prabhat Kumar Patel
Student ID:  11702041
Email Address: prabhat132000@gmail.com
Code: Mention solution code assigned to you
#include<stdio.h>
#include<conio.h>
struct Process
{
	int process_id;
	int burst_time;
};
void sorting(struct Process temp[] ,  int n)
{
	int a;
	int i , j ;
	temp[n].burst_time=9999;
	for(j= 0 ; j < n; j++)
	{
		for(i = 0 ; i<=j ; i++)
		{
			if(temp[i].burst_time > temp[i+1].burst_time)
			{
			a = temp[i+1].burst_time;
			temp[i+1].burst_time = temp[i].burst_time;
			temp[i].burst_time = a;
			}
		}
}	
}
void processWaitTime( struct Process arr[] , int n , int wt[])
{
	int i;
	wt[0] = 0; // initializing the 'process 1' waiting time as 0. 
	for(i = 1 ; i< n ; i++)
	{
		wt[i] = arr[i-1].burst_time + wt[i-1];
	}
}
void turnAroundTime(struct Process arr[] , int n , int wt[] , int tat[])
{
	int i;
	for(i = 0 ; i < n ; i++)
	{
		tat[i] = wt[i] + arr[i].burst_time; 
	}
}
void averageTime(struct Process arr[] , int n)
{
	int wt[n] , tat[n],i ;
	
	processWaitTime(arr , n , wt); //function call 
	
	turnAroundTime(arr , n , wt , tat) ; //function call
	
	printf("priority \tProcess\tBurst Time\tWaiting Time\tTurn Around Time\n ");
	
	for(i = 0 ; i< n ; i++){
		printf("%d\t%d\t%d\t%d\t%d\n",i+1, arr[i].process_id,arr[i].burst_time,wt[i] , tat[i]);}	
}
int main()
{  
int w;
printf("ENTER 1 TO RUN THE CODE 2 TO EXIT :");
printf("      ");
//printf("ENTER 2 TO EXIT");
scanf("%d",&w);
if(w==1)
{

   int i,z,j;

	label:
  	
	  
	printf("enter the no of processes:-");
	scanf("%d",&z);
	if(z<=0)
	{
		printf("error no of process must be >1 :");
		printf("         ");
		printf("press 3 to enter back :");
		scanf("%d",&j);
		goto label;
	}
	struct Process arr[z];
	for( i=0;i<z;i++)
	{
		printf("process  %d:-",i+1);
		printf("    ");
		printf("enter process id:");
		scanf("%d",&arr[i].process_id);
		x:
		printf("enter brust time: ");
scanf("%d",&arr[i].burst_time);
		if(arr[i].burst_time<=0)
		{
			printf("------error invalid brust time------------");
			goto x;
		}
	}
	int n = sizeof(arr) / 	sizeof(arr[0]);
	sorting(arr,n);
	averageTime(arr , n) ;

	 // function call
	 
}
	return 0;	
}
 
Description:
 Shortest job first (SJF) or shortest job next, is a scheduling policy that selects the waiting process with the smallest execution time to execute next. SJN is a non-preemptive algorithm.
•	Shortest Job first has the advantage of having minimum average waiting time among all scheduling algorithms.
•	It is a Greedy Algorithm.
•	It may cause starvation if shorter processes keep coming. This problem can be solved using the concept of aging.
•	It is practically infeasible as Operating System may not know burst time and therefore may not sort them. While it is not possible to predict execution time, several methods can be used to estimate the execution time for a job, such as a weighted average of previous execution times. SJF can be used in specialized environments where accurate estimates of running time are available.




1.	Algorithm:


1- Sort all the processes in increasing order 
   according to burst time.
2- Then simply, apply FCFS.

1.	Completion Time: Time at which process completes its execution.
2.	Turn Around Time: Time Difference between completion time and arrival time. Turn Around Time = Completion Time – Arrival Time
3.	Waiting  Time(W.T): Time Difference between turn around time and burst time.
Waiting Time = Turn Around Time – Burst Time

3.  Calculate complexity of implemented algorithm. (Student must specify complexity of each line of code along with overall complexity)
Description (purpose of use):
•	Among all the available processes, the process with smallest burst time has to be selected.
•	Min heap is a suitable data structure where root element contains the process with least burst time.
•	In min heap, each process will be added and deleted exactly once.
•	Adding an element takes log(n) time and deleting an element takes log(n) time.
•	Thus, for n processes, time complexity = n x 2log(n) = nlog(n)

4.  Explain all the constraints given in the problem. Attach the code snippet of the implemented constraint.
Code snippet:
  printf("enter the no of processes:-");
	scanf("%d",&z);
*The value of  N entered must be fit in the array[N],tat[N],wt[N];
*1<z<N;(Z  cannot be zero);
 
 
5.  If you have implemented any additional algorithm to support the solution, explain the need and usage of the same.  
Description:
void sorting(struct Process temp[] ,  int n)
{
	int a;
	int i , j ;
	temp[n].burst_time=9999;
	for(j= 0 ; j < n; j++)
	{
		for(i = 0 ; i<=j ; i++)
		{
			if(temp[i].burst_time > temp[i+1].burst_time)
			{
			a = temp[i+1].burst_time;
			temp[i+1].burst_time = temp[i].burst_time;
			temp[i].burst_time = a;
			}
		}
	}
	}

*used bubble sort to compare the burst time of the process and assign them to their required positions .
*no of comparions are N-1;
* Optimized Implementation: ...
          * Worst and Average Case Time Complexity: O(n*n). ...
          *  Best Case Time Complexity: O(n). ...
          *  Auxiliary Space: O(1)

6. Explain the boundary conditions of the implemented code.
Description:
1.if(arr[i].burst_time<=0) //This cannot be satisfied and prints error;
 *Because burst time of a program cannot be zero;
*If zero then it cant be run in the memory ;
*So this is one of the boundary condition;
	2.if(z<=0)
*z cannot be less than zero because no of are zero then total process .
* for(i = 1 ; i< n ; i++)
*The value of  I must be less than  n because we are having only the range N so it cant cross N.

7. Explain all the test cases applied on the solution of assigned problem.
Description:

printf("enter the no of processes:-");
	scanf("%d",&z);
//enter no of processes : 2;
	
printf("process id %d:-",i+1);
		printf("enter process id:");
scanf("%d",&arr[i].process_id);
//process id :1
 //Enter process id :21

printf("enter brust time: ");	
	scanf("%d",&arr[i].burst_time);
//enter brust time : 3

printf("ENTER 1 TO RUN THE CODE :/n");
printf("ENTER 2 TO EXIT");
scanf("%d",&w);
8.  Have you made minimum 5 revisions of solution on GitHub?






