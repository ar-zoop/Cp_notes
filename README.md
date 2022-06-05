# Strings
```
cin.ignore(numeric_limits<streamsize>::max(), '\n'); // used as fflush after taking int in and then for taking string in
getline(cin,arr);//input string
```

```
int i;
string temp;
temp+=to_string(i); //append to string
s.replace(pos,1,temp); // replace in string
```

# Subsequence Printing
## Recursion
```
#include <bits/stdc++.h>
using namespace std;

int arr[3]={1,2,1};
int n=3;
//all subsequence printing
void sub(vector<int>&v ,int idx){
    if(idx>=n) {
        for (auto x: v) cout<<x<<" ";
        cout<<endl;
        return;
    }
    v.push_back(arr[idx]);
    sub(v, idx+1);
    v.pop_back();
    sub(v,idx+1);
}

//all subsequence printing with sum=3
void sub2(vector<int>&v ,int idx,int sum){
    if(idx>=n) {
        if(sum==3) {
            for(auto x: v) cout<<x<<" ";
             cout<<endl;
           
        }
       
        return;
    }
    v.push_back(arr[idx]);
    sum+=arr[idx];
    sub2(v, idx+1,sum);
    v.pop_back();
    sum-=arr[idx];
    sub2(v,idx+1,sum);
}

// only 1 subsequence printing with sum=3
bool isFound(vector<int>&v, int idx, int sum){
    if(idx==n){
        if(sum==3){
            for(auto x: v) cout<<x<<" ";
            cout<<endl;
            return true;

        }
        return false;
    }
    //take
    v.push_back(arr[idx]);
    sum+=arr[idx];
    if(isFound(v, idx+1,sum)){
        return true;
    }
    //dont take
    v.pop_back();
    sum-=arr[idx];
    if(isFound(v, idx+1,sum)){
        return true;
    }
    //by default
    return false;
}

//count the subsequences with sum=k
int count(int idx, int sum){
    if(idx==n){
        if(sum==3){
            return 1;
        }
        else return 0;
    }
    //take
  
    sum+=arr[idx];
    int l=count(idx+1,sum);

    //dont take
    
    sum-=arr[idx];
    int r=count(idx+1,sum);
    
    return l+r;
}

int main(){
    vector <int> v;
    // sub(v,0);
    // sub2(v,0,0);
    isFound(v,0,0);
    // int c=count(0,0);
    // cout<<c;
    return 0;
}
```

# Backtracking
```
#include <bits/stdc++.h>
using namespace std;

//print for 1 to n but use backtracking
void backtracking(int n){
    if(n==0) return;
    backtracking(n-1);
    cout<<n;
}

//print for 1 to n but use backtracking
void bt(int i, int n){
    if(i>n)return;
    bt(i+1,n);
    cout<<i;
}

int main(){
    backtracking(5);
    cout<<endl;
    bt(1,7);
    return 0;
}
```

# Lexicographical Printing
```
#include <bits/stdc++.h>
using namespace std;

void fun(int i, int n){
    if(i>n) return;
    cout<<i<<endl;
    for(int j=0;j<10;j++){
        
        fun(i*10+j,n);
    }
    
}

int main(){
    int n=1000;
    for(int i=1;i<=9;i++){
        fun(i,n);
    }
    return 0;
}
```

# Math functions
## Prime factor
```
#include <stdio.h>
#include<math.h>
int main(){
    int n;
    printf("Enter number to find factors of: ");
    scanf("%d",&n);
    for (int i=2;i<=sqrt(n);i++){
        if(n%i==0){
            printf("%d %d ",i,n/i);
        }
    }
}
```
## GCD and LCM
```
#include <stdio.h>
int gcd(int,int);
int lcm(int,int);
int main(){
	int t,a,b,i,c,d;
	scanf("%d",&t);
	for(i=0;i<t;i++){
		scanf("%d%d", &a,&b);
		c=gcd(a,b);
		d=lcm(a,b);
		printf("%d %d\n",c,d);
	}
	return 0;
}

int gcd(int a, int b){	
	if (b>a){
		return gcd(b,a);
	}

	else if (b==0)
		return a;
	else	
		return gcd(b,a%b);
}

int lcm(int a, int b){
	int c=gcd(a,b);
	return (a/c)*(b/c)*c;

}

```
