---
layout: post
title: "BigInteger"
date: 2017-10-01 06:00:00
image: 'http://res.cloudinary.com/dk8luxah1/image/upload/c_scale,w_760,h_400/v1502208952/algorithm.jpg'
description: BigInteger 사용 방법.
category: 'JAVA'
tags:
- java
- algorithm
- biginteger
twitter_text: BigInteger 사용 방법.
introduction: BigInteger 사용 방법.
---


int 최대값 2147483647<br/>long 최대값 9223372036854775807

알고리즘 문제에서 100자리 수도 나올 수 있다면 BigInteger 사용해야겠죠?

- 더하기 : add()<br/>
- 빼기   : subtract()<br/>
- 곱하기 : multiply()<br/>
- 나누기 : divide()


```java
BigInteger big=new BigInteger("3000000000000");
BigInteger c=big.add(new BigInteger("341341234"));
System.out.println(c);
```




















