#include<iostream>
#include <string>
using namespace std;

void menu()
{
	
    cout<<"\nTo Add contact press 1"<<endl;
    cout<<"To Display contacts press 2"<<endl;
    cout<<"To Search a Contact press 3"<<endl;
    cout<<"To Delete Contact press 4"<<endl;
}

struct node
{
   string name,num;
   node *next;
};

node *head = NULL , *thenode , *address;
int a = 0 ;


void Mainfun()
{
    thenode = new node;

    cout<<"Enter Name:-";
    cin>>thenode->name;

    cout<<"Enter Number:-";
    cin>>thenode->num;

    thenode->next = NULL;
    if(head == NULL)
    {
        head = thenode;
        address = thenode;
    }
    else
    {
        address->next= thenode;
        address = thenode;
    }
}
void Display()
{
    if(head == NULL)
    {
        cout<<"No contact's found!"<<endl;
    }

    else
    {
		cout<<"Detail's"<<endl;
        node *dis = head ;
        while (dis != NULL)
        {
            cout<<"\nName:-"<<dis->name<<endl;
            cout<<"Number:-"<<dis->num<<endl;
            dis= dis->next;
            a++;
        }
        cout<<"Your Contacts are:-"<<a<<endl;
    }
}

void Search()
{
    node *search= head;
    string cont;
    int count = 1;
    cout<<"To Search Contact Enter Position:-";
    cin>>cont;
    bool found = false;

    if(head == NULL)
    {
        cout<<"Not Found!"<<endl;
    }

    else
    {
        while (search != NULL)
        {
            if(cont == search->name || cont == search->num)
            {
                cout<<"\n Name:-"<<search->name<<endl;
                cout<<"Number:-"<<search->num<<endl;
                found =true;
                break;
            }
            search = search->next;
            count++;
        }
    }

    if(found == true)
    {

        cout<<"Position of Contact =:-"<<count<<endl;
    }

    else
    {
        cout<<"Contact Not Found!"<<endl;
    }
}

void Delete() 
{
    int del ;
    node *cont;
    address = head;
    cout<<"To Delete Contact Enter Position:-"<<endl;
    cin>>del;

    if(head==NULL)
    {
        cout<<"List is Empty"<<endl;
    }

    else if (del>a)
    {
        cout<<"Invalid Position!"<<endl;
    }

    else if(del==0)
    {
        address = head;
        head = head->next;
        delete address;
        cout<<"Contact deleted!"<<endl;
    }

    else
    {
        for (int a = 1 ; a<del ; a++)
        {
            address = address->next;
        }
        cont = address->next;
        address->next = cont->next;
        delete cont;
        cout<<"Contact deleted"<<endl;
    }
}


void main()   //main finction
{
	cout<<"********************Welcome to the app********************"<<endl;
	cout<<"********************You are using contacts by Fahad********************"<<endl;
	cout<<"MENU"<<endl;

	 
    int b;
    while (true)
    {
        menu();
        cin>>b;

        switch (b)
        {
        case 1:
            Mainfun();
            break;

        case 2:
            a = 0;
            Display();
            break;

        case 3:
            Search();
            break;

        case 4:
            Delete();
            break;

        default:
		    cout<<"Select Again!"<<endl;
        }
    }
}
