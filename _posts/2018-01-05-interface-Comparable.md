---
layout: post
title: Interface Comparable
category: java[api]
description: Comparable 인터페이스의 간단한 정리
---

> class를 비교하거나 내가 원하는 조건으로 자료구조를 정렬할때 Comparable Interface를 사용해보자.

<!--description-->

-----------------------

### 기본구조

인터페이스 Comparable의 기본 구조
```
class Test implements Comparable<Test> {

	@Override
	public int compareTo(Test arg0) {
		// TODO Auto-generated method stub
		return 0;
	}
}
```

클래스가 Comparable을 상속받게 되면 compareTo 오버라이드 메소드를 가지게 된다. compareTo 메소드에서 정렬기준을 정하고 비교값을 반환하여 정렬시킨다.

-----------------------

### 예제

Person 클래스에서 정렬기준을 나이로 정하고, 오름차순으로 정렬하는 예제이다.
```
import java.util.ArrayList;
import java.util.Collections;

public class Main {

	public static void main(String[] args) {

		ArrayList<Person> arrayList = new ArrayList<Person>();
		arrayList.add(new Person("홍길동", 15));
		arrayList.add(new Person("김삿갓", 22));
		arrayList.add(new Person("전우치", 37));

		Collections.sort(arrayList);

		for (Person person : arrayList)
			System.out.println(person.getName() + "\t" + person.getAge());
	}
}

class Person implements Comparable<Person> {
	private String name;
	private int age;

	Person(String name, int age) {
		this.name = name;
		this.age = age;
	}

	public String getName() {
		return name;
	}

	public int getAge() {
		return age;
	}

	@Override
	public int compareTo(Person person) {
		// TODO Auto-generated method stub
		if (person.getAge() < this.age) {
			return 1;
		} else
			return -1;
	}
}
```

<span class="olive">결과화면</span>
```
홍길동	15
김삿갓	22
전우치	37
```

-----------------------

다음 예제는 나이를 기준으로 오름차순으로 정렬 후, 이름순서(사전순)으로 내림차순하는 예제이다.
```
import java.util.ArrayList;
import java.util.Collections;

public class Main {

	public static void main(String[] args) {

		ArrayList<Person> arrayList = new ArrayList<Person>();
		arrayList.add(new Person("홍길동", 15));
		arrayList.add(new Person("이순신", 15));
		arrayList.add(new Person("앙기모", 15));
		arrayList.add(new Person("김삿갓", 22));
		arrayList.add(new Person("전우치", 37));

		Collections.sort(arrayList);

		for (Person person : arrayList)
			System.out.println(person.getName() + "\t" + person.getAge());
	}
}

class Person implements Comparable<Person> {
	private String name;
	private int age;

	Person(String name, int age) {
		this.name = name;
		this.age = age;
	}

	public String getName() {
		return name;
	}

	public int getAge() {
		return age;
	}

	@Override
	public int compareTo(Person person) {
		// TODO Auto-generated method stub
		if (person.getAge() > this.age) {
			return -2;
		} else if (person.getAge() == this.age) {
			if (person.getName().compareTo(this.name) < 0)
				return -1;
			else
				return 0;
		} else
			return 1;
	}
}
```

<span class="olive">결과화면</span>
```
홍길동	15
이순신	15
앙기모	15
김삿갓	22
전우치	37

```


-----------------------

### Comment

굳이 Comparable을 이용한 정렬이 불필요하다면,

[배열]
- Arrays.sort(array)


[ArrayList]
- Collections.sort(arrayList)
- Collections.reverse(arrayList)

를 사용하여 간단하게 정렬할 수 있다.

