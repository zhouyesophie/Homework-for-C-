# Homework-for-C-

#include <stdio.h>
#include <stdlib.h>
#define N 30

void  Read(int score[],long number[],int n)
{
    int i=-1;
    do{
        i++;
        printf("input score:\n");
        scanf("%d",&score[i]);
        printf("input number:\n");
        scanf("%ld",&number[i]);
    }while(i<n-1);

    return;
}


int summ(int score[],int n)
{
    int i,sum=0;
    for(i=0;i<n;i++)
	{
    sum=sum+score[i];
	}
	return sum;
}


void DataSort(int score[],long number[],int n)
{
	int i,j,temp1,temp2;
	for(i=0;i<n-1;i++)
	{
		for(j=i+1;j<n;j++)
		{
			if(score[j]>score[i])
			{
				temp1=score[j],temp2=number[j];
				score[j]=score[i],number[j]=number[i];
				score[i]=temp1,number[i]=temp2;

			 }
		}
	}
}

void DataNumber(int score[],long number[],int n)
{
	int i,j,temp1,temp2;
	for(i=0;i<n-1;i++)
	{
		for(j=i+1;j<n;j++)
		{
			if(number[j]<number[i])
			{
				temp1=score[j],temp2=number[j];
				score[j]=score[i],number[j]=number[i];
				score[i]=temp1,number[i]=temp2;

			 }
		}
	}
}


void PrintStu(int score[],long number[],int n)
{
	int i;
	for(i=0;i<n;i++)
	{
		printf("score is %d,number is %ld\n",score[i],number[i]);
	}
}

int SearchNumber(int score[],long number[],int x,int n)
{
	int low=0,high=n-1,mid;
	DataNumber(score,number,n);
	while(low<=high)
	{
		mid=(high+low)/2;
		if(x>number[mid])
		low=mid+1;

		else if(x<number[mid])
		high=mid-1;

		else
		return mid;

	}
	return -1;
}


void Statistics(int score[],int n)
{	int i=0;
	int a=0;
	int b=0;
	int c=0;
	int d=0;
	int e=0;

	for(i=0;i<n;i++)
	{	if(score[i]>=90&&score[i<=100])
	a++;
	else if(score[i]>=80&&score[i<90])
	b++;
	else if(score[i]>=70&&score[i<80])
	c++;
	else if(score[i]>=60&&score[i<70])
	d++;
	else
	e++;
	}
	printf("优秀：  %d	%.2f%%\n",a,(float)a*100/n);
	printf("良好：  %d	%.2f%%\n",b,(float)b*100/n);
	printf("中等：  %d	%.2f%%\n",c,(float)c*100/n);
	printf("及格：  %d	%.2f%%\n",d,(float)d*100/n);
	printf("不及格：%d	%.2f%%\n",e,(float)e*100/n);
}


void List(int score[],long number[],int n)
{	int i;

	for(i=0;i<n;i++)
	{	printf("学号：%ld 分数：%d\n",number[i],score[i]);


	}

}






int main()
{   int score[N],n,i;
    long number[N];
    int choice,sum,average;


    do{ printf("1: 输入记录\n");
        printf("2: 总分与平均分\n");
        printf("3: 按成绩由高到低排列\n");
        printf("4: 按学号由小到大排列\n");
        printf("5: 按学号检索排名及成绩\n");
        printf("6: 统计分析\n");
        printf("7: 记录列表\(学号+成绩）+总分+平均分\n");
        printf("0: 退出\n");
        printf("请选择需要的功能：");
        scanf("%d",&choice);

            switch(choice)
            {
            case 1://读入学生的分数，学号，人数；
                printf("输入的总的学生数:");
                scanf("%d",&n);
                Read(score,number,n);
                break;

            case 2://计算总分，均分；
                sum=summ(score,n);
                average=sum/n;
                printf("总分为：%d\n",sum);
                printf("均分为：%d\n",average);
                break;

            case 3://成绩由高到低排列；
				DataSort(score,number,n);
				printf("成绩降序为:\n");
				PrintStu(score,number,n);
				break;

			case 4://按学号由大到小排列；
				DataNumber(score,number,n);
				printf("学号升序为：\n");
				PrintStu(score,number,n);
				break;

			case 5://按学号检索排名及成绩；
            int x;
				printf("please input number:");
				scanf("%d",&x);
				SearchNumber(score,number,n,x);
				printf("%ld的分数为%d\n",number[i+1],score[i+1]);
				break;

			case 6://统计分析；
				Statistics(score,n) ;
				break;

			case 7://记录列表；
			List(score,number,n);
				sum=summ(score,n);
                average=sum/n;
				printf("总分：%d\n",sum);
				printf("均分：%d\n",average);
			break;

			default://退出；
			 break;

            }

    }while(choice!=0);
    return 0;
}

