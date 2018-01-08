---
layout: post
title: 약수 알고리즘(Divisor Algorithm)
category: algorithm
description: 약수(divisor)를 구하는 다양하고 효율적인 방법을 알아보고 계속 업데이트 하자.
---

> 약수(divisor)를 구하는 다양하고 효율적인 방법을 알아보자.

<!--description-->

-----------------------

### 약수의 성질

임의의 정수 N의 약수 n(n ∈ N) 에서 n은 다음 성질들을 갖는다.
- ±1 ∈ N
- ±n ∈ N
- N % n = 0




-----------------------

### Code 1_1

약수를 구하는 가장 기본적인 코드
```java
public static void main(String[] args) {

	Scanner sc = new Scanner(System.in);
	int N = sc.nextInt();

	for(int i=1;i<=N;i++)
		if(N%i==0) System.out.println(i);
}
```


-----------------------

### Code 1_2

Code1_1은 1부터 N까지 탐색하여 약수를 판별한다. Code1_2에서는 N의 약수중에 최대값은 N이고 그 다음의 최대값이 될 수 있는 값은 아무리 크더라도 N/2라는 점을 사용하였다.

```java
for (int i = 1; i <= N / 2; i++)
	if (N % i == 0)
		System.out.println(i);
System.out.println(N);
```
반복 횟수가 절반이 되어 효율을 높일 수 있다.



-----------------------

### Code 2_1

약수의 개수를 구하는 기본적인 코드, Code1_2와 동일하다.

```java
public static void main(String[] args) {

	Scanner sc = new Scanner(System.in);

	int N = sc.nextInt();
	int cnt = 1;

	for (int i = 1; i <= N / 2; i++)
		if (N % i == 0)
			cnt++;

	System.out.println(cnt);

}
```



-----------------------

### Code 2_2

1부터 n까지 정수 중에 약수의 개수가 가장많은 정수를 구할때는 Code2_1 기본형을 통해 간단하게 구현할 수 있다.
```java
public class Main {

	public final static int MAXNUM = 101;
	public static int[] arr = new int[MAXNUM];

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);

		for (int i = 1; i < MAXNUM; i++) {
			int cnt = 1;

			for (int j = 1; j <= i / 2; j++)
				if (i % j == 0)
					cnt++;

			arr[i] = cnt;
		}
	}
}
```
위 알고리즘은 n*(n/2)의 시간 복잡도를 갖는다.




-----------------------

### Code 2_3

코드 2_2는 정수 n값이 커질수록 부담이된다. 1부터 n까지의 약수의 개수를 구하는 상황에서 배수를 응용하면 무의미하게 반복하는 과정을 줄일 수 있다.
```java
public class Main {

	public final static int MAXNUM = 101;
	public static int[] arr = new int[MAXNUM];

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);

		for(int i=1;i<MAXNUM;i++){
			for(int j=1;j<MAXNUM/i;j++){
				arr[i*j]++;
			}
		}
	}
}
```
n, n/2, n/3 ···· n/n 만큼 반복을 수행하여 시간복잡도를 줄일 수 있다.



-----------------------

### 백준 2986 파스칼

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);

		int n = sc.nextInt();
		int result = 1;

		for (int i = n / 2;; i--) {
			if (n == 1) break;
			if (n % i == 0) {
				result = n - i;
				break;
			}
		}

		System.out.println(result);
	}
}
```



-----------------------

### Comment

약수에 대한 알고리즘은 계속 추가할 예정.