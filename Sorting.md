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
## Selection Sort

```
void selectionsort(vector<int>&v , int n)
{
    for(int i=0 ;i<n ;i++)
    {
    int mini=i;
        for(int j=i+1 ;j<n ;j++)
        {
            if(v[j]<v[mini])mini=j;
        }
        swap(v[i],v[mini]);
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
    selectionsort(v,n);
    cout<<"After sorting"<<endl;
    print(v,n);
    return 0;
}
```
## Counting Sort
```
#include<bits/stdc++.h>
using namespace std;
int main()
{
    int n,i,j,x,y;
    cout << "Enter no.of elements" << endl;
    cin >> n;
    vector<int> arr(n);
    for(i=0;i<n;i++) // loop to take array input
    {
        cin >> arr[i];
    }
    map<int,int> frequency; // declaring map 
    for(i=0;i<n;i++) //loop to store unique element and its frequency in map
    {
        if(frequency.find(arr[i])==frequency.end()) //checking if elements already exist in map
        {
            frequency[arr[i]]=1; // if no, count of the element is 1
        }
        else
        {
            frequency[arr[i]]++; // if yes, count of the element is incremented
        }
    }
    map<int,int> :: iterator itr;
    i=0;
    for(itr=frequency.begin();itr!=frequency.end();itr++) // iterating to each element of the map
    {
        x=itr->first; // itr->first contains the array element
        y=itr->second; // itr->second contains its frequency
        for(j=0;j<y;j++) // loop to change next y elements of array to x
        {
            arr[i++]=x; // changing ith element of array to x and incrementing i
        }
    }
    for(i=0;i<n;i++) // printing sorted array
    {
        cout << arr[i] << " ";
    }
    return 0;
}
or
// Counting sort in C++ programming

#include <iostream>
using namespace std;

void countSort(int array[], int size) {
  // The size of count must be at least the (max+1) but
  // we cannot assign declare it as int count(max+1) in C++ as
  // it does not support dynamic memory allocation.
  // So, its size is provided statically.
  int output[10];
  int count[10];
  int max = array[0];

  // Find the largest element of the array
  for (int i = 1; i < size; i++) {
    if (array[i] > max)
      max = array[i];
  }

  // Initialize count array with all zeros.
  for (int i = 0; i <= max; ++i) {
    count[i] = 0;
  }

  // Store the count of each element
  for (int i = 0; i < size; i++) {
    count[array[i]]++;
  }

  // Store the cummulative count of each array
  for (int i = 1; i <= max; i++) {
    count[i] += count[i - 1];
  }

  // Find the index of each element of the original array in count array, and
  // place the elements in output array
  for (int i = size - 1; i >= 0; i--) {
    output[count[array[i]] - 1] = array[i];
    count[array[i]]--;
  }

  // Copy the sorted elements into original array
  for (int i = 0; i < size; i++) {
    array[i] = output[i];
  }
}

// Function to print an array
void printArray(int array[], int size) {
  for (int i = 0; i < size; i++)
    cout << array[i] << " ";
  cout << endl;
}

// Driver code
int main() {
  int array[] = {4, 2, 2, 8, 3, 3, 1};
  int n = sizeof(array) / sizeof(array[0]);
  countSort(array, n);
  printArray(array, n);
}
```

