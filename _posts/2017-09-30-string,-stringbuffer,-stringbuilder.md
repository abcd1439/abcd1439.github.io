---
layout: post
title: "String, StringBuffer, StringBuilder"
date: 2017-09-30 11:51:23
image: 'http://res.cloudinary.com/dk8luxah1/image/upload/c_scale,w_760/v1502208952/coding.jpg'
description: String, StringBuffer, StringBuilder 를 알아봅시다.
category: 'JAVA'
tags:
- java
- string
- stringbuffer
- stringbuilder
twitter_text: String, StringBuffer, StringBuilder 를 알아봅시다.
introduction: String, StringBuffer, StringBuilder 를 알아봅시다.
---
#**String**

String 클래스는 변경 불가능한 클래스입니다. 예로 substring() 메소드를 적용하면 또 하나의 String 객체가 생성됩니다. 그렇기에 시스템 자원을 낭비하는 경향이 있습니다.

String 클래스의 장점은 특별한 안전장치 없이도 안전하게 공유될 수 있습니다. 대부분 복잡한 문자열 처리과정보다 한번 설정된 문자열들을 공유하는 경우가 많아 자바에서는 기본 문자열을 String 클래스로 설정하였습니다.


- - -
#**StringBuffer**

StringBuffer 클래스는 변경이 가능한 클래스입니다. 새로운 객체를 생성하지 않지만 단순한 참조에서는 상대적으로 String보다 나쁜 성능을 보입니다. 따라서, 단순 참조가 많은 경우 String클래스가 유리합니다.<br />StringBuffer 객체의 생성이 시간과 메모리 자원을 가장 많이 필요로합니다.<br /> StringBuffer 객체의 생성 및 toString() 메소드를 통한 String 객체의 생성을 반드시 필요로 하므로 한번의 문자열 추가할 때는 오히려 String보다 시간 및 메모리 자원 낭비를 초래합니다.


- - -
#**StringBuilder**

StringBuffer 클래스와 StringBuilder 클래스에서 제공하는 메소드는 동일합니다.<br/>StringBuffer 클래스는 여러 스레드에서 안전하게 사용 가능합니다.<br />StringBuilder 클래스는 단일 스레드에서의 안전성만을 보장합니다.(여러개의 스레드에서 하나의 StringBuilder 객체를 처리하면 문제가 발생.)


- - -
###**정리**

1. 변하지 않는 문자열은 String을 사용.<br />
2. StringBuffer 멀티쓰레드로 접근하거나 문자열이 변경될 경우 사용.<br />
3. StringBuilder는 비동기방식이기 때문에 싱글 스레드 환경하에서 변화되는 문자열로 사용.<br />






















