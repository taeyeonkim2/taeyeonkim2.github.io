---
layout: post
title: 2023-6-12-ezen
categories: 수업-자바
---


<h3>JAVA</h3>

```1=java
    Set<String> set=new HashSet<>();
    
    set.add("홍길동");
		set.add("고길동");
		set.add("김길동");
		set.add("최길동");	
		set.add("홍길동");
		set.add("김길동");
		set.add("이길똥");
    
    Iterator<String> it=set.iterator(); //Iterator 객체 생성
		while(it.hasNext()) {//다음 element 있니?
			System.out.println(it.next()); //다음 element 줘
		}
    if(set.contains("홍길똥")) { //set에 "홍길동"이 저장되어있니?
			System.out.println("있어");
		}else System.out.println("없어");
    
    if(set.remove("홍길동")) { //홍길동 삭제할 수 있니?
			System.out.println("삭제완료");
		}else System.out.println("삭제불가");
    
    String[] names=set.toArray(new String[set.size()]);
		for(int i=0;i<names.length;i++) {
			System.out.println(names[i]);
		}
		System.out.println();
    
    Object[] arr=set.toArray(); //Set<String> set을 Object형 배열에 넣는다.
		for(Object ob: arr) {
			System.out.println(ob);
		}
    
```
```1=java
    Set<String> set=new HashSet<>();
		//객체 저장
		set.add("Java");
		set.add("JDBC");
		set.add("Servlet/JSP");
		set.add("Java");			//<-- 중복 객체이므로 저장하지 않음
		set.add("iBATIS");
		
		//저장된 객체 수 출력
		System.out.println(set.size());
		Iterator<String> it=set.iterator();
		while(it.hasNext()) {
			System.out.println(it.next());
		}
    for(String str: set) {
			System.out.println(str);
		}
```
**Iterator 사용법 숙지하기

<h3>좋은 예시</h3>
```1=java
package ch15.sec03.exam02;

public class Member {
	public String name;
	public int age;

	public Member(String name, int age) {
		this.name = name;
		this.age = age;
	}
				
	//hashCode 재정의
	@Override
	public int hashCode() {
		return name.hashCode() + age;
	}

	//equals 재정의
	@Override
	public boolean equals(Object obj) {
		if(obj instanceof Member target) {
			//target?? obj를 다운캐스팅해서 target이라는 변수를 생성한거야 
			//ex) Member target= (Member) obj; 
			return target.name.equals(name) && (target.age==age) ; 
      //new로 생성해서 다른 객체여도 내용물이 같으면 같은 걸로 생각하겠다!
		} else {
			return false;
		}
	}
}
```
```1=java
  package ch15.sec03.exam02;

import java.util.*;
	
public class HashSetExample {
	public static void main(String[] args) {
		//HashSet 컬렉션 생성
		Set<Member> set=new HashSet<>();
		//Member 객체 저장
		set.add(new Member("홍길동", 30));
		set.add(new Member("홍길동", 30));
		//얘네는 분명히 다른 객체야!! 그런데, equals를 재정의해서 같은 걸로 볼거야
    //그러면 Member클래스의 equals를 주석 처리하면 다른 객체로 보겠지??
		//저장된 객체 수 출력		
		System.out.println("총 객체 수 : " + set.size());
    //Member클래스의 equals를 주석처리 하면 -> 2
    //주석처리 안하면 -> 1
	}
}
```
<h3>얘도 중요</h3>
package ch15.sec03.exam03;

import java.util.*;

public class HashSetExample {
	public static void main(String[] args) {
		//HashSet 컬렉션 생성
		Set<String> set = new HashSet<String>();
		
		//객체 추가
		set.add("Java");
		set.add("JDBC");
		set.add("JSP");
		set.add("Spring");
		
		//객체를 하나씩 가져와서 처리 : Iterator 이용 "JSP"문자열 삭제하기
		Iterator<String> it=set.iterator();
		while(it.hasNext())	{
			if(it.next().equals("JSP")) {
				it.remove();
			}
		}
		//객체 제거 "JDBC"
		it=set.iterator();
		while(it.hasNext())	{
			if(it.next().equals("JDBC")) {
				it.remove();
			}
		}
		//개선된 for 문 이용 출력하기
		for(String str:set) {
			System.out.println(str);
		}
		
	}
}

##HashSet
  
```1=java
   package ch15.sec04.exam01;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Map.Entry;
import java.util.Set;

public class HashMapExample {
	public static void main(String[] args) {
		//Map 컬렉션 생성
		Map<String, Integer> map = new HashMap< >();

		//객체 저장
		map.put("신용권", 85); //85는 Integer로 오토박싱
		map.put("홍길동", 90);
		map.put("동장군", 80);
		map.put("홍길동", 95); //키값은 하나만 있어야되는데??-> 동일한 키가 존재하면 업데이트해버린다.
		System.out.println("총 Entry 수: " + map.size());
		System.out.println();

		//키로 값 얻기
		String key = "홍길동";
		int value = map.get(key); //"홍길동"(키) 넣어서 키-값table의 value값을 빼오자.
		System.out.println(key + ": " + value);
		System.out.println();

		//키 Set 컬렉션을 얻고, 반복해서 키와 값을 얻기
		Set<String> keySet = map.keySet(); //키-값table의 키를 전부 가져와서 keySet에 키들만 저장
		Iterator<String> keyIterator = keySet.iterator(); //String을 담는 Set인 keySet의 Iterator 객체 생성
		while (keyIterator.hasNext()) {
			String k = keyIterator.next(); //키 하나를 가져와서 k에 담고
			Integer v = map.get(k); //담은 키를 넣어서 키-값table의 value값을 빼오자.
			System.out.println(k + " : " + v);
		}
		System.out.println();

		//엔트리 Set 컬렉션을 얻고, 반복해서 키와 값을 얻기
		Set<Entry<String, Integer>> entrySet = map.entrySet();
		Iterator<Entry<String, Integer>> entryIterator = entrySet.iterator();
		while (entryIterator.hasNext()) {
			Entry<String, Integer> entry = entryIterator.next();
			String k = entry.getKey();
			Integer v = entry.getValue();
			System.out.println(k + " : " + v);
		}
		System.out.println();
		
		//키로 엔트리 삭제
		map.remove("홍길동"); 
		//키값을 넣어서 키에 맞는 value 값을 삭제해라. value를 사용하지않고 키를 사용해서 삭제
		System.out.println("총 Entry 수: " + map.size());
		System.out.println();
	}
}
```
-HashTable은 HashMap이랑 다 똑같은데 멀티스레드를 지원한다.

<h2>제일 중요</h2>
```eclipse
  package ch15.sec05.exam03;

public class Person implements Comparable<Person> {
	public String name;
	public int age;

	public Person(String name, int age) {
		this.name = name;
		this.age = age;
	}

	@Override
	public int compareTo(Person o) {
		if(age<o.age) return -1;
		else if(age == o.age) return 0;
		else return 1;
	}
   package ch15.sec05.exam03;

import java.util.TreeSet;

public class ComparableExample {
	public static void main(String[] args) {
		//TreeSet 컬렉션 생성
		TreeSet<Person> treeSet = new TreeSet<Person>();

		//객체 저장
		treeSet.add(new Person("홍길동", 45));
		treeSet.add(new Person("감자바", 25));
		treeSet.add(new Person("박지원", 31));
		
		//비교할 Person 객체생성
		Person p=new Person("비교자", 30);
		
		//객체를 하나씩 가져오기
		for(Person person : treeSet) {
			System.out.println(person.name + ":" + person.age);
			if(person.compareTo(p)==0) {
				System.out.println("동갑");
			}else if(person.compareTo(p)==-1) {
				System.out.println("비교자가 더 나이 많아");
			}else {
				System.out.println("비교자가 더 어려");
			}
		}
		
		
	}
```
  ##ch15.sec05.exam04 / ch15.exam08 얘도 꼭 공부하기

  
 


