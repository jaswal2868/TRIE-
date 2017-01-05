#include <iostream>
#include <stdlib.h>
#include <string>


#define INDEX(c) ((int)c - (int)'a')

#define FREE(p) \
    free(p);    \
    p = NULL;
using namespace std;
struct node
{
    node *ptr[26];
    bool isleaf;
};
void insertnode(node *head,string s)
{
    int i,j;

    for(i=0;i<s.size();i++)
    {
       if((head->ptr[s[i]-'a'])==NULL)
       {
           node *p=new node;

           for(j=0;j<26;j++)
            p->ptr[j]=NULL;
           p->isleaf=false;
           head->ptr[s[i]-'a']=p;
           head=p;
       }
       else
        head=head->ptr[s[i]-'a'];
    }
    head->isleaf=true;

}
void search_string(node *head,string s)
{
    int i;
for(i=0;i<s.size();i++)
{
    if(head->ptr[s[i]-'a']==NULL)
        {cout<<"Not present\n";

        return;}
    else
    {head=head->ptr[s[i]-'a'];

    }
}
if(head->isleaf)
{
        cout<<"present\n";
}    else
        cout<<"Not Present\n";
}
int leafNode(node *head)
{
    return (head->isleaf != false);
}

int isItFreeNode(node *head)
{
    int i;
    for(i = 0; i < 26; i++)
    {
        if( head->ptr[i] )
            return 0;
    }

    return 1;
}


bool delete_main(node *head,string s,int level,int len)
{
if( head )
    {

        if( level == len )
        {
            if( head->isleaf )
            {

                head->isleaf=false;


                if( isItFreeNode(head) )
                {
                    return true;
                }

                return false;
            }
        }
        else
        {
            int index = INDEX(s[level]);

            if( delete_main(head->ptr[index], s, level+1, len) )
            {

                FREE(head->ptr[index]);


                return ( !leafNode(head) && isItFreeNode(head) );
            }
        }
    }

    return false;
}
void delete_word(node *head,string s)
{
int len =s.size();
if(len>0)
{
    delete_main(head,s,0,len);
}
}


int main()
{
node *head =new node;
int i;
for(i=0;i<26;i++)
    head->ptr[i]=NULL;
        head->isleaf=false;
string s;
int ch;
while(1)
{
    cout<<"------Main Menu---------\n";
    cout<<"Choose from following options\n";
    cout<<"1.insert word into trie\n";
    cout<<"2.search word in trie\n";
    cout<<"3.delete word from trie\n";
    cout<<"4.exit\n";
 cin>>ch;
    switch(ch)
    {
    case 1:cin>>s;
           insertnode(head,s);
           break;

    case 2:cout<<"enter string to check\n";
           cin>>s;
              search_string(head,s);
             break;

    case 3:cout<<"enter string to be deleted\n";
    cin>>s;
    delete_word(head,s);
    break;

    case 4: exit(0);
            break;

    default : cout<<"wrong choice entered\n";

    }


}

    return 0;
}
