#include<iostream>
#include<string.h>
using namespace std;
typedef struct student{
    int roll;
    char name[20];
    float SGPA;
}stud;
void create (stud s[20],int n);
void display (stud s[20],int n);
void bubbles (stud s[20],int n);
void lsearch(stud s[20],int n,float key);
int main (){
    stud s[20];
    int key,n,ch;
    do{
        cout<<"1.Create student database."<<endl;
        cout<<"2.Display student database."<<endl;
        cout<<"3.Bubble sort"<<endl;
        cout<<"4.Linear search "<<endl;
        cout<<"5.Exit"<<endl;
        cout<<"Enter your choice : ";
        cin>>ch;

        switch(ch){
            case 1 :
            cout<<"Enter The Number Of Records :";
            cin>>n;
            create(s,n);
            break;
            case 2 :
            display(s,n);
            break;
             case 3 :
             bubbles(s,n);
             break;
             case 4 :
             cout<<"\nEnter the marks u want to search : ";
             cin>>key;
             lsearch(s,n,key);
             break;
            case 5 : exit (0);
        default :
        cout<<"\nEnter the valid choice !";
        }
    }while(ch!=5);  
}
void create(stud s[20],int n){
    int i;
    for(i=0;i<n;i++){
    cout<<"Enter the Roll Number of student : ";
    cin>>s[i].roll;
    cout<<"Enter the Name of student :";
    cin>>s[i].name;
    cout<<"Enter the SGPA :";
    cin>>s[i].SGPA;
    }
}
void display(stud s[20],int n){
    int i;
    cout<<"\n"<<"\t"<<"ROLL"<<"\t"<<"NAME"<<"\t"<<"SGPA"<<endl;
    for(i=0;i<n;i++){
        cout<<"\n";
        cout<<"\t"<<s[i].roll<<"\t"<<s[i].name<<"\t"<<s[i].SGPA<<endl;
    }
    } 
    void bubbles(stud s[20],int n){
        int i,j;
        stud temp;
        for(i=0;i<n;i++){
            for(j=0;j<n;j++){
                if(s[j].roll>s[j+1].roll){
                    temp=s[j];
                    s[j]=s[j+1];
                    s[j+1]=temp;
                }
            }
        }
    }
    void lsearch(stud s[20],int n,int key){
        int i;
        cout<<"\n"<<"\t"<<"ROLL"<<"\t"<<"NAME"<<"\t"<<"SGPA"<<endl;
        for(i=0;i<n;i++){
        if (key==s[i].SGPA){
            cout<<"\t"<<s[i].roll<<"\t"<<s[i].name<<"\t"<<s[i].SGPA<<endl;
             }
        }
    }