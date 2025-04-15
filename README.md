# PTA_7-16
# 求符合条件的整数集
# 给定不超过6的正整数A，考虑从A开始的连续4个数字。请输出所有由它们组成的无重复数字的3位数。

# 输入格式：输入在一行中给出A。
# 输出格式：输出满足条件的的3位数，要求从小到大，每行6个整数。整数间以空格分隔，但行末不能有多余空格。
```cpp
#include<iostream>

using namespace std;
int main() {
	int a;
	cin >> a;
	if (a > 6) {
		cout << "Error" << endl;
		return 0;
	}
	int b[4];
	b[0] = a;
	b[1] = a + 1;
	b[2] = a + 2;   //也可写成 int b[4] = { a , a + 1 , a + 2 , a + 3 };
	b[3] = a + 3;
 
	int count = 0;

	for (int i = 0;i < 4;i++) {
		for (int j = 0;j < 4;j++) {
			if (i == j)continue;  //如果百位十位相等就跳过本次循环
		
			for (int k = 0;k < 4;k++) {
				if (k == i || k == j)continue;
				int number = b[i] * 100 + b[j] * 10 + b[k];
				cout << number;
				count++;

				if (count % 6 == 0) {  //每行输出6个数后换行
					cout << endl;
				}
				else {
					cout << " ";
				}
			}
		}
	}
	return 0;
}