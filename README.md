# C-p36-5-
C语言学习笔记 p36 指针详解(5)
#include<stdio.h>
//计算器
void menu()
{
    printf("****************************\n");
    printf("******1.add    2.sub  ******\n");
    printf("******3.mul    4.div  ******\n");
    printf("******    0.exit      ******\n");
    printf("****************************\n");
}
int Add(int x,int y)
{
    return x+y;
}
int Sub(int x,int y)
{
    return x-y;
}
int mul(int x,int y)
{
    return x*y;
}
int Div(int x,int y)
{
    return x/y;
}
int main()
{
    int input=0;
    int x=0;
    int y=0;
    do
    {
        menu();
        printf("请选择：>");
        scanf("%d",&input);
        printf("请输入两个操作数：>");
        scanf("%d%d",&x,&y);
        switch(input)
        {
            case 1:
               printf("请输入两个操作数：>");
               scanf("%d%d",&x,&y);
               printf("%d\n", Add(x,y));
               break;
            case 2:
                printf("请输入两个操作数：>");
                scanf("%d%d",&x,&y);
                printf("%d\n",Sub(x,y));
                break;
            case 3:
                printf("请输入两个操作数：>");
                scanf("%d%d",&x,&y);
                printf("%d\n",Mul(x,y));
                break;
            case 4:
                 printf("请输入两个操作数：>");
                 scanf("%d%d",&x,&y);
                 printf("%d\n",Div(x,y));
                 break;
              case 0:
                  printf("退出\n");
                  break;
              default:

                  printf("选择错误\n");
                  break;
        }
    }while(input);
    return 0;
}//这里可以函数指针数组来简化



//指向函数指针数组的指针
int main()
{
    int arr[10]={0};
    int (*p)[10]=&arr;//取出数组的地址

    int (*pfArr[4])(int,int);//pfArr是一个数组-函数指针的数组
    int(*(*ppfArr)[4])(int,int)=&pfArr;
    //ppfArr是一个赎罪指针，指针指向的数组有4个元素
    //指向的数组的每个元素的类型是一个函数指针int(*)(int,int)
    return 0;
}


//回调函数
//回调函数就是一个通过函数指针调用的函数
void Calc(int(*pf)(int,int))
{
    int x=0;
    int y=0;
     printf("请输入两个操作数：>");
     scanf("%d%d",&x,&y);
     printf("%d\n",pf(x,y));
}

int main()
{
    //上面的main的case语句就调用相对应的Calc函数就行了
    return 0;
}
    //用回调函数就很好的解决了上面代码冗余的问题

void print(char* str)
{
    printf("hehe:%s",str);
}
void test(void (*p)(char*))
{
    printf("test\n");
    p("bit");
}
{
}
int main()
{
    test(print);
    return 0;
}


void BubbleSort(int arr[],int sz)
{
    //...
}
//qsort-可以排序任意类型的函数
int main()
{
    //冒泡排序函数
    //冒泡排序函数只能排序整形函数数组
    int arr[]={1,3,5,7,9,2,4,6,8,0};
    int sz=sizeof(arr)/sizeof(arr[0]);
    BubbleSort(arr,sz)
}
