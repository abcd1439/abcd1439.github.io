---
layout: post
title: "BufferedReader"
date: 2017-10-01 08:00:00
image: 'http://res.cloudinary.com/dk8luxah1/image/upload/c_scale,w_760/v1502208952/coding.jpg'
description: BufferedReader 를 알아봅시다.
category: 'JAVA'
tags:
- java
- bufferedreader
twitter_text: BufferedReader 를 알아봅시다.
introduction: BufferedReader 를 알아봅시다.
---


BufferedReader 를 통해 입력받을때 유의할 점.<br/>
1. 기본적으로 BufferedReader는 한 줄을 통째로 입력받는 방법으로 주로 쓰입니다.
2. readLine() 메서드는 값을 읽어올 때, String값으로 개행문자(엔터값)를 포함해 한줄을 전부 읽어오는 방식입니다.
3. read() 메서드는 값을 읽어올 때, int값으로 변형하여 읽어오는 방식입니다.

&#45; 예를들어 1이라는 숫자를 read()를 통해 읽어오면 int형 숫자 1을 읽어오는 것이 아닌, ASCII 형식의 문자값 '1'을 읽어오는 것이므로 결국 int값으론 49를 읽어오는 것이 됩니다.

&#45; 그래서 보통 int a = Integer.parseInt(br.readLine()); 를 통해 엔터값을 포함해 한줄을 통째로 입력받은 뒤 해당 스트링값을 int로 형변환 해준다.