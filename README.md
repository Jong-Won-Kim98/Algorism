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

14. 자연수를 입력 받으면 그 수를 뒤집어 소수일 경우 출력하시오.(단, 끝 수가 0일 경우 0은 무시하고 출력한다.)
```C++
#include <iostream>
using namespace std;

int reverse(int x) {
	int res = 0, tmp;
	while (x > 0) {
		tmp = x % 10;
		// 입력 받은 자연수를 첫번째 자리 숫자 부터 저장하기 위함
		res = res * 10 + tmp;
		// 0으로 초기화한 res를 첫번째 자리수 인 tmp를 더해줌으로 숫자를 반전 시킨다.
		x = x / 10;
	}
	return res;
}

bool isPrime(int x) {
	int i;
	if (x == 1) return false;
	bool flag = true;
	for (i = 2; i < x; i++) {
		if (x % i == 0) {
			flag = false;
			break;
		}
	}
	return flag;
}
int main() {
	int i, num, n, tmp;
	cin >> n;

	for (i = 1; i <= n; i++) {
		cin >> num;
		tmp = reverse(num);
		if (isPrime(tmp)) cout << tmp << " ";
	}
	return 0;
}
```

15. 1보다 큰 자연수를 입력받고 1부터 n까지 소수의 개수를 출력받으시오.
```C++
#include <iostream>
using namespace std;

int main() {
	int n, i, j, flag, count = 0;
	//flag: 깃발 역활로 소수일 경우 1 소수가 아닐경우 0으로 초기화하여 구분한다.
	cin >> n;
	for (i = 2; i <= n; i++) {
		flag = 1;
		for (j = 2; j*j <= i; j++) {
			if (i % j == 0) {
				break;
			}
		}
		if (flag == 1) count++;
	}
	cout << count;
	return 0;
}
```

16. Anagram, 두 문자열이 알파벳의 나열 순서를 다르지만 그 구성이 일치하면 두 단어를 아나그램이라고 합니다, 두 문자열이 아나그램일 경우 Yes 아닐 경우 No를 출력하시오
```C++
#include <iostream>
#include <algorithm>
using namespace std;
char a[60], b[60];
// 알파벳 소문자 + 대문자를 각 배열의 인덱스 번호에 알파벤 순서로 저장하여 해당 인덱스의 알파벳이 나올경우 ++
int main() {
	int i;
	char S1[101];
	cin >> S1;

	for (i = 0; S1[i] != '\0'; i++) {
		if (S1[i] >= 65 && S1[i] <= 90) {
			a[S1[i] - 64]++;
			//대문자일 경우 a배열 해당 인덱스에 ++
		}
		else a[S1[i] - 70]++;
		//소문자일 경우
	}
	cin >> S1;
	for (i = 0; S1[i] != '\0'; i++) {
		if (S1[i] >= 65 && S1[i] <= 90) {
			b[S1[i] - 64]++;
		}
		else b[S1[i] - 70]++;
	}
	for (i = 1; i <= 52; i++) {
		if (a[i] != b[i]) {
			cout << "No";
			exit(0);
		}
	}
	cout << "Yes";
	return 0;
}
```

17. 개수를 입력한 후 1부터 m까지의 합을 구하는 알고리즘을 짜시오.
```C++
#include <iostream>
using namespace std;

int main() {
	int n, sum = 0, i, j, m, ans;
	//n = 학생 수, ans = 학새이 제출한 정답 sum = 실제 정답
	cin >> n;

	for (i = 1; i <= n; i++) {
		cin >> m >> ans;
		sum = 0;
		for(j = 1; j <= m; j++) {
			sum += j;
		}
		if (ans == sum) cout << "Yse";
		else cout << "No";
	}
	return 0;
}
```

18. 시간과 경보음이 울리는 기준을 입력한 후 시간동안 연속으로 몇초의 경보음이 울렸는지 측정하는 알고리즘을 짜시오.
```C++
#include <iostream>
using namespace std;

int main() {
	int n, count = 0, i, max = -2146000000, val, a;
	// n = 입력된 시간, max = 연속적으로 울린 경보음을 측정하기 위한 시간, val = 경보음 기준
	cin >> n >> val;
	for (i = 1; i <= n; i++) {
		cin >> a;
		if (a > val) count++;
		else count == 0;
		if (count > max) max = count;
	}
	if (max == 0) max = -1;
	cout << max;
	return 0;
}
```

19. 한 줄에 앉아 있는 학생의 키 정보가 입력될 경우 뒷 사람보다 큰 사람이 몇명이 있는지 구하시오.
```C++
#include <iostream>
using namespace std;

int main() {
	int i, n, max = -2147000000, a[101], count=0;
	cin >> n;
	for (i = 1; i <= n; i++) {
		cin >> a[i];
	}
	max = a[n];
	for (i = n - 1; i >= 1; i--) {
		if (max < a[i]) {
			max = a[i];
			count++;
		}
	}
	cout << count;
	return 0;
}
```

20. 두 사람이 가위바위보를 했을 때 경우의 수를 입력하고 승자를 출력하시오.
```C++
#include <iostream>
using namespace std;

int main() {
	int n, i, a[101], b[101];

	cin >> n;

	for (i = 0; i < n; i++) {
		cin >> a[i];
	}
	for (i = 0; i < n; i++) {
		cin >> b[i];
	}
	for (i = 0; i < n; i++) {
		if (a[i] == b[i]) cout << "D" << endl;
		else if (a[i] == 1 && b[i] == 3) cout << "A" << endl;
		else if (a[i] == 2 && b[i] == 1) cout << "A" << endl;
		else if (a[i] == 3 && b[i] == 2) cout << "A" << endl;
		else cout << "B" << endl;
	}
	return 0;
}
```

21. 두 사람의 입력된 숫자를 비교하여 이긴 사람은 승점 3점을 가져가고 비길 경우 모두 승점 1을 가져감으로 최종 승자를 구하시오.(단, 승점이 같은 경우 마지막 라운드의 승자가 우승한다)
```C++
#include <iostream>
using namespace std;

int main() {
	int res = 0, a[11], b[11], cntA = 0, cntB = 0, i, n;

	cin >> n;
	for (i = 0; i < n; i++) {
		cin >> a[i];
	}
	for (i = 0; i < n; i++) {
		cin >> b[i];
	}
	for (i = 0; i < n; i++) {
		if (a[i] > b[i]) {
			cout << "A ";
			cntA = cntA + 3;
			res = 1;
		}
		else if (a[i] == b[i]) {
			cout << "D ";
			cntA = cntA +1;
			cntB = cntB +1;
		}
		else {
			cout << "B ";
			cntB = cntB + 1;
			res = 2;
		}

	}
	if (cntA == cntB) {
		if (res == 1) cout << "A";
		else cout << "B";
	}
	else if (cntA > cntB) cout << "A";
	else cout << "B";
	
	return 0;
}
```

22. n, k가 입력되고 n일 만큼의 날짜 동안 k일 만큼 연속적으로 차이가 나는 최대 온도를 구하시오.
```C++
#include <iostream>
#include <vector>
using namespace std;

int main() {
	int n, k, i, sum = 0, max = -2147000000;
	cin >> n >> k;
	vector<int> a(n);
	// 배열 a의 동적 할당 형태

	for (i = 0; i < n; i++) {
		cin >> a[i];
	}
	for (i = 0; i < k; i++) {
		sum += a[i];
	}
	max = sum;
	for (i = k; i < n; i++) {
		sum = sum + (a[i] - a[i - k]);
		if (sum > max) max = sum;
	}
	cout << max;
	return 0;
}
```

23. n개의 자연수를 입력하고 상향구간의 개수를 출력하시오.
```C++
#include <iostream>
#include <vector>
using namespace std;

int main() {
	int n, i, pre, now, cnt = 1, max = -2147000000;
	cin >> n >> pre;

	for (i = 2; i <= n; i++) {
		cin >> now;
		if (now >= pre) {
			cnt++;
			if (cnt > max) max = cnt;
		}
		else cnt = 1;
		pre = now;
	}
	cout << max;

	return 0;

}
```

24. 유쾌한 점퍼 문제
```C++
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
	int n, i, res, pre, now;
	cin >> n;
	vector<int> a(n);

	cin >> pre;

	for (i = 1; i < n; i++) {
		cin >> now;
		res = abs(pre - now);
		//abs: 연산값으 절댓값을 출력하는 함수
		if (res > 0 && res < n && a[res] == 0) a[res] = 1;
		//만약 뺄셈의 결과가 모두 다르고 범위내일 경우 벡터 a에 저장한 후 중복을 확인한다.
		else {
			cout << "No";
			return 0;
		}
		pre = now;
	}
	cout << "Yes";
	return 0;
}
```

25. 1~100의 자연수 n을 입력하고 n개의 자연수가 입력 되었을 때 등수를 출력하시오(단, 같은 숫자일 경우 높은 석차로 동일하게 처리한다.)
```C++
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
int main() {
	int n, i, j, b[101];
	cin >> n;
	vector<int> a(n);

	for (i = 0; i < n; i++) {
		cin >> a[i];
		b[i] = 1;
	}

	for (i = 0; i < n; i++) {
		for (j = 0; j < n; j++) {
			if (a[i] > a[j]) b[j]++;
		}
	}
	for (i = 0; i < n; i++) {
		cout << b[i] << " ";
	}

	return 0;
}
```

26. 마라톤 문제 (현재 n명의 선수가 달리고 있고 현재 달리고 있는 순서대로 각 선수들의 평균 실력을 입력했을 때 각 선수들의 마지막 최고로 올라갈 수 있는 순위를 예측하는 프로그램)
```C++
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
	int n, i, j, cnt;
	cin >> n;
	vector<int> a(n+1);
	
	for (i = 1; i <= n; i++) {
		cin >> a[i];
	}
	cout << 1;
	for (i = 2; i <= n; i++) {
		cnt = 0;
		for (j = i - 1; j >= 1; j--) {
			if (a[j] >= a[i]) cnt++;
		}
		cout << cnt + 1 << " ";
	}
	return 0;
}
```

27. N!의 표현법
```C++
#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;

int main() {
	int n, i, j, tmp;
	cin >> n;
	vector<int> ch(n + 1);
	for (i = 2; i <= n; i++) {
		tmp = i;
		j = 2;
		while (1) {
			if (tmp % j == 0) {
				tmp = tmp / j;
				ch[j]++;
			}
			else j++;
			if (tmp == 1) break;
			// 소인수 분해를 통하여 소수들의 개수를 파악
		}
	}
	cout << n << "!" << " =";
	for (i = 2; i <= n; i++) {
		if (ch[i] != 0) cout << ch[i] << " ";
	}
	return 0;
}
```

