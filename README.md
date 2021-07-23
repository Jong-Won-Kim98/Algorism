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

6. 문자열을 입력 받고 문자열에서 자연수를 찾아 자연수의 약수를 출력하시오.
```C++
#include <iostream>
using namespace std;

int main() {
	char a[100];
	int res = 0, cnt = 0, i;

	cin >> a;

	for (i = 0; a[i] != '\0'; i++) {
		if (a[i] >= 48 && a[i] <= 57) {
			// a[i] != '\0': 배열 a의 끝 인덱스 번호인 공백을 만날경우
			res = res * 10 + (a[i] - 48);
		} 
	}
	cout << res << endl;
	for (i = 1; i <= res; i++) {
		if (res % i == 0) cnt++;
	}
	cout << cnt;
	return 0;
}

```

7. 문자열을 입력받고 문자열에 공백이 있을경우 지우고 대문자가 있을경우 소문자로 변환하여 출력한다.
```C++
#include <iostream>

using namespace std;

int main() {
	char a[101], b[101];
	int i, p = 0;
	gets_s(a);

	for (i = 0; a[i] != '\0'; i++) {
		if (a[i] != ' ') {
			if (a[i] >= 65 && a[i] <= 90) {
				b[p++] = a[i] + 32;
			}
			else b[p++] = a[i];
		}
	}
	
	b[p] = '\0';
	cout << b;
	return 0;
}

```

8. 문자열을 입력받아 괄호의 '(' 와 ')'의 짝이 맞을 경우 "Yes"를 맞지 않을 경우 "No"를 출력하시오.
```C++
#include <iostream>
using namespace std;

int main() {
	char a[31];
	int i, cnt = 0;

	cin >> a;
	
	for (i = 0; a[i] != '\0'; i++) {
		if (a[i] == '(') cnt++;
		else if (a[i] == ')') cnt--;
		if (cnt < 0) break;
	}
	if (cnt == 0) cout << "Yes";
	else  cout << "No";
		
	return 0;
}

```