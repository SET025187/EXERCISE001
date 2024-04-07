![](C:\Users\set\AppData\Roaming\Typora\typora-user-images\image-20240403095552174.png)

![image-20240403095546312](C:\Users\set\AppData\Roaming\Typora\typora-user-images\image-20240403095546312.png)

![image-20240403095555974](C:\Users\set\AppData\Roaming\Typora\typora-user-images\image-20240403095555974.png)

![image-20240403095602092](C:\Users\set\AppData\Roaming\Typora\typora-user-images\image-20240403095602092.png)

```
\#include <bits/stdc++.h>
using namespace std;
using ll=long long;

const int N = 5e3+9;

int a[N];

bool dp[N][N];

void solve()
{
	int n;cin>>n;
	for(int i=1;i<=n;i++)cin>>a[i];
	
	dp[0][0]=true;
	for(int i=1;i<=n;i++)//i 表示当前处理的数据元素的下标
	{
		for(int j=0;j<=5e3;j++)// j 表示当前和的取值
		{
			//复制
			dp[i][j]=dp[i-1][j];
			//新增
			if(j>=a[i])dp[i][j] |= dp[i-1][j-a[i]];//|=按位或
		}
	}	
	ll ans=0;
	for(int i=0;i<=5e3;i++)if(dp[n][i])ans++;
	cout<<ans<<'\n';
}

int main()
{
	ios::sync_with_stdio(0),cin.tie(0),cout.tie(0);	
	int _=1;
	while(_--)solve();
	return 0;
}
```

![image-20240403101932267](C:\Users\set\AppData\Roaming\Typora\typora-user-images\image-20240403101932267.png)

![image-20240403101215468](C:\Users\set\AppData\Roaming\Typora\typora-user-images\image-20240403101215468.png)

```
\#include <bits/stdc++.h>
using namespace std;
using ll=long long;

const int N = 5e3+9,M=5e5+9;//5e3*100

int a[N];
bool dp[M];

void solve()
{
	int n;cin>>n;
	for(int i=1;i<=n;i++)cin>>a[i];
	
	dp[0]=true;
	for(int i=1;i<=n;i++)//i 表示当前处理的数据元素的下标
	{
		for(int j=5e5;j>=a[i];--j)// j 表示当前和的取值 从后往前
		{
			//新增
			dp[j] |= dp[j-a[i]];//|=按位或
		}
	}
	
	ll ans=0;
	for(int i=0;i<=5e5;i++)if(dp[i])ans++;
	cout<<ans<<'\n';
}

int main()
{
	ios::sync_with_stdio(0),cin.tie(0),cout.tie(0);
	
	int _=1;
	while(_--)solve();
    
	return 0;
}
```

![image-20240403102853010](C:\Users\set\AppData\Roaming\Typora\typora-user-images\image-20240403102853010.png)

![image-20240403102915819](C:\Users\set\AppData\Roaming\Typora\typora-user-images\image-20240403102915819.png)

![image-20240403114648116](C:\Users\set\AppData\Roaming\Typora\typora-user-images\image-20240403114648116.png)

![image-20240403120033895](C:\Users\set\AppData\Roaming\Typora\typora-user-images\image-20240403120033895.png)

```
\#include <bits/stdc++.h>
using namespace std;
using ll=long long;

const int N = 5e3+9,M=5e5+9;//5e3*100
int a[N];

void solve()
{
	int n;cin>>n;
	for(int i=1;i<=n;i++)cin>>a[i];
	
	bitset<M> bs;//位集合，表示二进制位序列。
	bs[0]=1;//初始低位是1
	for(int i=1;i<=n;i++)//i 表示当前处理的数据元素的下标
	{
		bs|=(bs<<a[i]);//在dp数组中时右移,但在bs中时左移
	}	
	cout<<bs.count()<<'\n';
}

int main()
{
	ios::sync_with_stdio(0),cin.tie(0),cout.tie(0);
	
	int _=1;
	while(_--)solve();
	return 0;
}
```

