---
layout: post
title: "Some articles are just so short that we have to make the footer stick"
categories: ALGORITHM
---


##유클리드 호제법

1.두 정수의 최대공약수를 구하는 알고리즘

-두 정수가 같아질 때까지 큰 쪽에서 작은 쪽을 뺀다.

내가 푼 것
```1=java
  while(true){
   if(n1>n2){
    n1 -= n2;
   }else if(n1<n2){
    n2 -= n1;
   }else{//n1==n2
    return n1;}
   }//while
```

책 답안
```1=java
  while(a!=b){
    if(a>b){
    a -= b;
    }else{
    b -= a;
    }
   }//while
```

2. 최소공배수를 구하는 알고리즘

내가 푼 것

-두 정수: a,b  두 정수를 보관할 변수 : num1, num2 최소 공배수: m = a * b / 최대공약수
```1=java
  int num1=a;
  int num2=b;
  
   while(a!=b){
    if(a>b){
    a -= b;
    }else{
    b -= a;
    }
   }//while
   m = num1 * num2 / a;
```

3.선형 검색 알고리즘

-임의의 배열에서 원하는 데이터를 찾는 알고리즘

-pos=-1로 초기화

내가 푼 것
```1=java
    int a[]= {72,68,92,88,41,53,97,84,39,55};
		int pos=-1;
		int key=23;
		
		for(int i=0;i<a.length;i++) {
			if(a[i]==key) {pos=i; break;}
		}
		if(pos!=-1) {
			System.out.println("a["+pos+"]");
		}else {
			System.out.println("찾는 수가 없습니다.");
		}
```

책 답안
```1=java
    int a[]= {72,68,92,88,41,53,97,84,39,55};
		int x,i,pos;
    
    Scanner sc=new Scanner(System.in);
    x=sc.nextInt();
    pos=-1;
    sc.close();
    
    for(i=0;i<a.lenght && <strong>pos==-1</strong>;i++){
       if(a[i] == x){
        pos=i;
       }
     }
```
