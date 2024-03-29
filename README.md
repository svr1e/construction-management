//construction-management
//c program to calculate total Contruction cost
#include <stdio.h>
struct details
{
int plotno;
char landholdername[100];
int phno;
}d;
struct quantity
{
float tons,price,total;
int gst;
char materialname[20];
}a[100];
struct items
{
char itemname[100];
float mrp;
float workercharges,toatl;
struct electricity
{
char itemname[100];
float mrp;
float workercharges,toatl;
}c;
}b[100];
struct pumbing
{float mrp,workercharges;
char itemname[100];
}e[100];
int constructionmaterial(struct quantity s);
int main()
{int i,n;
printf("enter name of the name of land owner");
scanf("%s",d.landholdername);
printf("enter plot number");
scanf("%d",d.plotno);
printf("enter the phone number");
scanf("%d",d.phno); 
printf("enter total num of times all the materials expoted");
scanf("%d",&n);
for(i=0;i<=n;i++)
{
printf("enter name of the material");
scanf("%s",a[i].materialname);
printf("enter number of tons");
scanf("%d",&a[i].tons);
printf("enter price per ton ");
scanf("%f",&a[i].price);
printf("enter gst percent ");
scanf("%d",&a[i].gst);
}

}
