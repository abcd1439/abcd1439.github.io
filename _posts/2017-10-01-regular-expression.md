---
layout: post
title: "정규표현식"
date: 2017-10-01 09:00:00
image: 'http://res.cloudinary.com/dk8luxah1/image/upload/c_scale,w_760,h_400/v1502208952/algorithm.jpg'
description: 정규표현식을 배워봅시다.
category: 'JAVA'
tags:
- java
- algorithm
- regular expression
twitter_text: 정규표현식을 배워봅시다.
introduction: 정규표현식을 배워봅시다.
---

<table>
	<thead>
    	<tr>
        	<th>정규표현식</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
    	<tr>
        	<td>?</td>
            <td>물음표는 0번 또는 1차례까지의 발생을 의미한다. 이를테면 colou?r는 "color"와 "colour"를 둘 다 일치시킨다.</td>
        </tr>
        <tr>
        	<td>&#42;</td>
            <td>별표는 0번 이상의 발생을 의미한다. 이를테면 ab*c는 "ac", "abc", "abbc", "abbbc" 등을 일치시킨다.</td>
        </tr>
        <tr>
        	<td>+</td>
            <td>덧셈 기호는 1번 이상의 발생을 의미한다. 이를테면 ab+c는 "abc", "abbc", "abbbc" 등을 일치시키지만 "ac"는 일치시키지 않는다.</td>
        </tr>
        <tr>
        	<td>^</td>
            <td>바로 뒤의 문자열로 시작</td>
        </tr>
        <tr>
        	<td>$</td>
            <td>바로 앞의 문자열로 종료</td>
        </tr>
        <tr>
        	<td>[]</td>
            <td>[] 안에 있는 문자 중 하나, 범위는 -로 지정.
            1. 숫자만 : ^[0-9]*$
            2. 영문자만 : ^[a-zA-Z]*$
            3. 한글(완성형)만 : ^[가-힣]*$
            4. 영어와 숫자만 : ^[a-zA-Z0-9]*$
            </td>
        </tr>
        <tr>
        	<td>\s</td>
            <td>공백 문자</td>
        </tr>
        <tr>
        	<td>\S</td>
            <td>공백 문자가 아닌 나머지 문자</td>
        </tr>
        <tr>
        	<td>\w</td>
            <td>알파벳이나 숫자</td>
        </tr>
        <tr>
        	<td>\W</td>
            <td>알파벳이나 숫자를 제외한 문자</td>
        </tr>
        <tr>
        	<td>\d</td>
            <td>숫자 [0-9]와 동일</td>
        </tr>
        <tr>
        	<td>\D</td>
            <td>숫자를 제외한 모든 문자</td>
        </tr>
        <tr>
        	<td>\</td>
            <td>정규표현식 역슬래시(\)는 확장 문자<br/>역슬래시 다음에 일반 문자가 오면 특수문자로 취급하고 역슬래시 다음에 특수문자가 오면 그 문자 자체를 의미</td>
        </tr>
    </tbody>
</table>






* * *
# 활용

이 정규표현식들은 split(), replace(), replaceAll() 메소드를 통해 활용할 수 있습니다. 메소드 안에 정규표현식을 넣음으로써 문자열에 포함된 숫자를 제거나 교체 등 활용이 가능합니다.

replace()란 일치하는 첫 번째 값만 교체해주며 replaceAll()은 일치하는 모든 것을 바꾸어 줍니다.














