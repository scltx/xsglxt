//包含头文件
#include <iostream>
#include<string.h>
#include<stdio.h>
using namespace std;
//定义数据类型
struct student
{
    char sno[13];
    char name[30];
    int mathscore;
    int englishscore;
    int chinesescore;
    int totalscore;
};
//宏定义
#define M 100
//函数声明
int menu();
void input(struct student a[]);
void output(struct student a[]);
int select(struct student a[]);
void InsertRecord(struct student a[]);
void DeleteRecord(struct student a[]);
void ModifyRecord(struct student a[]);
void tj(struct student a[]);
//主函数
int num;
int main()
{
    struct student a[M];//定义a数组用于存储学生信息
    int choice; //定义变量用于存储菜单选项
    //调用函数格式:函数名（实参）
    num=0;
    do
    {
        choice=menu();//调用menu()函数，在屏幕上打印主菜单，并将用户输入的选项值存储到变量choice中
        switch(choice)//根据用户选择的菜单项完成对应的功能
        {
        case 0:break;
        case 1:input(a);break;  //调用input()函数，完成录入功能
        case 2:output(a);break; //调用output()函数，完成显示功能
        case 3:select(a);break;
        case 4:select(a);break;
        case 5:select(a);break;
        case 6:select(a);break;
        case 7:tj(a);break;   //调用查询函数

        }

    }while(choice!=0);





    return 0;
}
int menu()
{
    int choice;
    printf("______________学生成绩管理系统————————————————————————————————\n");
    printf("                    1 录入\n");
    printf("                    2 显示\n");
    printf("                    3 查询\n");
    printf("                    4 添加\n");
    printf("                    5 删除\n");
    printf("                    6 修改\n");
    printf("                    7 统计\n");
    printf("                    0 退出\n");
    printf("请输入菜单选项：");
    scanf("%d",&choice);
    return choice;
}
void input(struct student a[])
{
    char x;
    int i=0;
    do
    {


        printf("请输入学号：");
        scanf("%s",a[i].sno);
        printf("请输入姓名：");
        scanf("%s",a[i].name);
        printf("请输入数学成绩：");
        scanf("%d",&a[i].mathscore);
        printf("请输入英语成绩：");
        scanf("%d",&a[i].englishscore);
        printf("请输入语文成绩：");
        scanf("%d",&a[i].chinesescore);
        getchar();
        a[i].totalscore=a[i].mathscore+a[i].englishscore+a[i].chinesescore;

        printf("是否继续录入（y or n）：");
        scanf("%c",&x);
        num++;
        i++;
    }while(x=='y');
}

void output(struct student a[])
{
   printf("学号      姓名      数学成绩  英语成绩  语文成绩  总成绩\n");
   for(int i=0;i<num;i++)
   {
       printf("%-10s%-10s%-10d%-10d%-10d%-10d\n",a[i].sno,a[i].name,a[i].mathscore,a[i].englishscore,a[i].chinesescore,a[i].totalscore);
   }
}
int select(struct student a[])
{
    int i;
    char xh[13];
    printf("请输入学号：");
    scanf("%s",xh);
    for(i=0;(i<num)&&(strcmp(xh,a[i].name));i++);
    if(i<num)
           printf("%-10s%-10s%-10d%-10d%-10d%-10d\n",a[i].sno,a[i].name,a[i].mathscore,a[i].englishscore,a[i].chinesescore,a[i].totalscore);
    else
    {
        printf("没有此人！"); i=-1;
    }

    return i;

}
void InsertRecord(struct student a[])
{
        printf("请输入学号：");
        scanf("%s",a[num].sno);
        printf("请输入姓名：");
        scanf("%s",a[num].name);
        printf("请输入数学成绩：");
        scanf("%d",&a[num].mathscore);
        printf("请输入英语成绩：");
        scanf("%d",&a[num].englishscore);
        printf("请输入语文成绩：");
        scanf("%d",&a[num].chinesescore);
        num++;
}
void DeleteRecord(struct student a[])
{
    int i;
    i=select(a);
    if(i==-1) return;
    for(int j=i;j<num;j++)
        a[j]=a[j+1];
    num--;
}
void ModifyRecord(struct student a[])
{
    int i;
    i=select(a);
    if(i==-1) return;
    printf("请输入学号：");
    scanf("%s",a[i].sno);
    printf("请输入姓名：");
    scanf("%s",a[i].name);
    printf("请输入数学成绩：");
    scanf("%d",&a[i].mathscore);
    printf("请输入英语成绩：");
    scanf("%d",&a[i].englishscore);
    printf("请输入语文成绩：");
    scanf("%d",&a[i].chinesescore);
}
void tj(struct student a[])
{
     int i,ensumscore=0,chsumscore=0,masumscore=0;
     double cj=0,ej=0,mj=0,cl=0,el=0,ml=0,cy=0,ey=0,my=0;
     int mx=0,mn;
     double enpj,chpj,mapj,cyx,myx,eyx,clh,mlh,elh,cjg,mjg,ejg;
     for(i=0;i<num;i++){
        if(a[i].totalscore>mx)
            mx=a[i].totalscore;
     }
     mn=a[0].totalscore;
      for(i=0;i<num;i++){
        if(a[i].totalscore<mn)
            mn=a[i].totalscore;
     }
      for(i=0;i<num;i++){
        chsumscore+=a[i].chinesescore;
     }
     chpj=chsumscore/num;
     for(i=0;i<num;i++){
        masumscore+=a[i].mathscore;
     }
     mapj=masumscore/num;
     for(i=0;i<num;i++){
        ensumscore+=a[i].englishscore;
     }
     enpj=ensumscore/num;
      for(i=0;i<num;i++){
        if(a[i].mathscore>=60)
            mj++;
        if(a[i].englishscore>=60)
            ej++;
        if(a[i].chinesescore>=60)
            cj++;
     }
     mjg=mj/num;
     cjg=cj/num;
     ejg=ej/num;
    for(i=0;i<num;i++){
        if(a[i].mathscore>=80)
            ml++;
        if(a[i].englishscore>=80)
            el++;
        if(a[i].chinesescore>=80)
            cl++;
     }
     mlh=ml/num;
     clh=cl/num;
     elh=el/num;
    for(i=0;i<num;i++){
        if(a[i].mathscore>=90)
            my++;
        if(a[i].englishscore>=90)
            ey++;
        if(a[i].chinesescore>=90)
            cy++;
     }
     myx=my/num;
     cyx=cy/num;
     eyx=ey/num;
     printf("数学平均成绩   及格率   良好率   优秀率\n");
     printf("%g,%g,%g,%g\n",mapj,mjg,mlh,myx);
     printf("语文平均成绩   及格率   良好率   优秀率\n");
     printf("%g,%g,%g,%g\n",chpj,cjg,clh,cyx);
     printf("英语平均成绩   及格率   良好率   优秀率\n");
     printf("%g,%g,%g,%g\n",enpj,ejg,elh,eyx);
     printf("最高分    最低分\n");
     printf("%d,%d\n",mx,mn);


}






