# Algorism
 
 > C++ Algorism

 1. 1~n까지의 m의 배수함
```c++
#include <iostream>
using namespace std;
int main()
{
	int n, m, i, sum = 0;

	cin >> n >> m;
	for (i = 1; i <= n; i++) {
		if (i % m==0)
			sum += i;
	}
	cout << sum;
	return 0;

}
```

2. 자연수의 합
```c++
#include <iostream>
using namespace std;

int main() {
	int a, b, i, sum = 0;

	cin >> a >> b;
	for (i = a; i < b; i++) {
		cout << i << " + ";
		sum += i;
	}
	cout << b << " = ";
	cout << sum + b;
	return 0;

}
```

3. 진약수의 합
```c++
#include <iostream>
using namespace std;

int main()
{
	int a, i, sum = 0;

	cin >> a;
	cout << "1";
	for (i = 2; i < a; i++) {
		if (a % i == 0) {
			cout << " + " << i;
			sum += i;
		}
	}
	cout << " = " << sum + 1;

	return 0;
}
```

4. 입력된 나이 중 가장큰 값과 적은 값의 차이 구하기
```c++
#include <iostream>
using namespace std;

int main()
{
	int n, i, a, max = -2147000000, min = 2147000000;
	// int 변수형의 최소 값: -2147000000, 최대 값: 2147000000
	cin >> n;
	for (i = 1; i <= n; i++) {
		cin >> a;
		if (a > max) max = a;
		if (a < min) min = a;
	}
	cout << max - min;
	return 0;
}
```

5. 주민등록 번호에 따른 나이 계산, 성별 판별하기
```C++
#include <iostream>
using namespace std;

int main() {
	char a[20];
	string s;
	int year, age;

	cin >> a;

	if (a[7] == '1' || a[7] == '2') {
		year = 1900 + ((a[0] - 48) * 10 + (a[1] - 48));
	}
	else {
		year = 2000 + ((a[0] - 48) * 10 + (a[1] - 48));
	}
	if (a[7] == '1' || a[7] == '3') {
		s = "Man";
	}
	else {
		s = "Girl";
	}
	age = 2021 - year + 1;
	cout << "year: " << year << endl;
	cout << "age: " << age << endl;
	cout << s;
	return 0;
}
```
