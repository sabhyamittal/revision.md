## Bubble Sort
```
#include<bits/stdc++.h>
#include <iostream>

using namespace std;


void bubblesort(vector<int>&v , int n)
{
    for(int i=0 ;i<n ;i++)
    {
        bool swapped=false;
        for(int j=0 ;j<n-i-1 ;j++)
        {
        if(v[j]>v[j+1])
        {
        swap(v[j],v[j+1]);
        swapped=true;
        }
        }
        if(swapped==false)break;
    }
}
void print(vector<int>&v,int n)
{
    for(int i=0 ;i<n ;i++)
    {
        cout<<v[i]<<" ";
    }
    cout<<endl;
}

int main()
{
    int n;
    cin>>n;
    vector<int>v;
    for(int i=0 ;i<n ;i++)
    {
        int num;
        cin>>num;
        v.push_back(num);
    }
    cout<<"Before sorting"<<endl;
    print(v,n);
    bubblesort(v,n);
    cout<<"After sorting"<<endl;
    print(v,n);
    return 0;
}
```
