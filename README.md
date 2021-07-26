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
		
	return

``` 

9. 입력한 자연수까지의 약수를 구하시오.
```C++
int main()
{
	int num, i, j, cnt;

	cin >> num;

	for (i = 1; i <= num; i++)
	{
		cnt = 0;
		for (j = 1; j <= i; j++) {
			if (i % j == 0) cnt++;
		}
		cout << cnt;
	}
	return 0;
}
// 위 코드는 작은 숫자에서는 잘 돌아가지만 num에 큰 수를 대입할 경우 알고리즘의 시간 복잡도가 너무 커져 시간이 오래 걸린다.
```

```C++
#include <iostream>
using namespace std;
int cnt[50001];
// 전역번수
int main() 
{
	int num, i, j;

	cin >> num;

	for (i = 1; i <= num; i++) {
		for (j = i; j <= num; j = j + i) {
			cnt[j]++;
		}
	}
	for (i = 1; i <= num; i++) {
		cout << cnt[i];
	}
	return 0;
	// cnt배열을 생성하고, i의 배수인 수를 카운트 +1 해줌으로서 알고리즘의 시간 복잡도를 줄이는 방법
}
```

10. n개의 자연수를 입력하고 자릿수의 합이 가장 큰 수를 출력하시오
```C++
#include <iostream>
using namespace std;
int digit_sum(int x) {
	int tmp, sum = 0;
	while (x>0)
	{
		tmp = x % 10;
		sum += tmp;
		x = x / 10;
		// x를 10으로 나눈 후 나머지를 tmp에 저장하고 sum으로 tmp를 누적하여 더하는 함수
	}
	return sum;
}
int main()
{
	int n, num, i, sum, max = -2147000000, res;
	cin >> n;
	for (i = 0; i < n; i++) {
		cin >> num;
		sum = digit_sum(num);
		if (sum > max) {
			max = sum;
			res = num;
		}
		else if (sum == max) {
			if (num > res) res = num;
		}
	}
	cout << res;
	return 0;
}
```

11. 자연수 n을 입력하고 각 자연수의 자릿수를 총 합하시오.
```C++
#include <iostream>
using namespace std;

int main()
{
	int num, i, res, cnt=0;

	cin >> num;
	for (i = 1; i <= num; i++) {
		res = i;
		while (res > 0) {
			res = res / 10;
			cnt++;
		}
	}
	cout << cnt;

	return 0;
}
```

12. 자연수 n을 입력한 후 몇개의 숫자를 사용했는지 구하시오.
```C++
#include <iostream>
using namespace std;
int main()
{
	int num, count = 1, d = 9, res = 0, sum = 0;
	// count: 입력된 자연수 n의 자릿수
	// d: 최대 자릿수를 구하기 위한 값 ex) 0+9=9, 90+9=99
	cin >> num;

	while (sum + d < num) {
		res = res + (count * d);
		sum = sum + d;
		count++;
		d = d * 10;
	}
	res = res + ((num - sum) * count);
	cout << res;
	return 0;
}
```

13. n자리 자연수 중 가장 많이 사용된 숫자를 출력하시오.
```C++
int main()
{
	int i, num, max = -2147000000, res;
	char a[101];
	// 입력된 자연수를 자리별로 하나하나 읽기 위한 배열
	cin >> a;

	for (i = 0; a[i] != '\0'; i++); {
		num = a[i] - 48;
		// 문자열 배열 a에 저장되어 있기 때문에 아스키 코드 번호로 받아들여 -48을 해준다.
		ch[num]++;
	}
	for (i = 0; i <= 9; i++) {
		if (ch[i] >= max) {
			max = ch[i];
			res = i;
		}
	}
	cout << res;
	return 0;
}
```
