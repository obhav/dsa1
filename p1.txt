#include<iostream>
#include<string.h>
//#include<process.h>
using namespace std;
typedef struct student{
    int roll;
    char name[20];
    float SGPA;
}stud;
void create(stud s[20],int n);
void display(stud s[20],int n);
void insertion(stud s[20],int n);
int bsearch(stud s[20],char x[20],int low,int high);
int main(){
    stud s[20];
    int n,ch,key,result;
    char x[20];

   do{
    cout<<"1.create student database  "<<endl;
    cout<<"2.Display student data  "<<endl;
    cout<<"3.Insertion sort  "<<endl;
    cout<<"4.Binary search"<<endl;
    cout<<"5.Exit "<<endl;
    cout<<"Enter your chioce : "<<endl;
    cin>>ch;
    switch(ch){
        case 1 :
        cout<<"\nHow many students : ";
        cin>>n;
        create(s,n);
        break;
        case 2 :
        display(s,n);
        break;
        case 3 :
        insertion(s,n);
        break;
        case 4 : 
        cout<<"Enter the name of student u want to search :"<<endl;
        cin>>x;
        insertion(s,n);
        result=bsearch(s,x,0,(n-1));
        if(result==-1){
            cout<<"\nStudent name u want to search for is not present !\n";
        }
        else{
            cout<<"\nThe Student is presrnt  \t"<<s[result].name<<endl;
        }
        break; 
        case 5 : exit (0);
        default :
        cout<<"\nEnter the valid choice !";
    }


   }while(ch!=5); 
}
void create(stud s[20],int n){
    int i ;
    for(i=0;i<n;i++){
        cout<<"Enter student roll : ";
        cin>>s[i].roll;
        cout<<"Enter student name : ";
        cin>>s[i].name;
        cout<<"Enter student SGPA : ";
        cin>>s[i].SGPA;

    }
}
void display(stud s[20],int n){
    int i;
    cout<<"\n"<<"\t"<<"Roll.no"<<"\t"<<"Name"<<"\t"<<"SGPA"<<endl;
    for(i=0;i<n;i++){
        cout<<"\n"<<"\t"<<s[i].roll<<"\t"<<s[i].name<<"\t"<<s[i].SGPA<<endl;
    }
}
void insertion(stud s[20],int n){
    int i,j;
    stud key ;
    for(i=1;i<n;i++){
         key=s[i];
         j=i-1;
         while(j>=0 && strcmp(s[j].name,key.name)>0){
            s[j+1]=s[j];
            j--;

         }
         s[j+1]=key;
    }
}
int bsearch(stud s[20],char x[20],int low ,int high){
    int mid;
    while(low<=high){
        mid=(low+high)/2;
        if(strcmp(x,s[mid].name)==0){
            return mid;
        }
        else if (strcmp(x,s[mid].name)<0){
            high =mid-1;
        }
        else {
            low=mid+1;
        }
    }
    return -1;
}