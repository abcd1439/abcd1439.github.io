---

layout: post

title: "유클리드 호제법(GCD, LCM)"

date: 2017-10-06 06:00:00

image: 'http://res.cloudinary.com/dk8luxah1/image/upload/c_scale,w_760,h_400/v1507302402/gcdlcm.jpg'

description: 유클리드 호제법(GCD, LCM)을 배워봅시다.

category: 'JAVA'

tags:

- java

- algorithm

- gcd

- lcm

- 유클리드 호제법

twitter_text: 유클리드 호제법(GCD, LCM)을 배워봅시다.

introduction: 유클리드 호제법(GCD, LCM)을 배워봅시다.

---

## 최대공약수GCD, Greatest Common Divisor<br/>최소공배수 LCM, Least Common multiple

위 사진을 보시면 쉽게 이해하실 수 있을거예요!

이해가 되셨다면 코드로 바꿔볼까요?

[백준 GCD, LCM 2609번](https://www.acmicpc.net/problem/2609)


```java
		int a, b;
		int multiple;
		int mod = 0;
		int GCD = 0, LCM = 0;

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

		StringTokenizer st = new StringTokenizer(br.readLine());

		a = Integer.parseInt(st.nextToken());
		b = Integer.parseInt(st.nextToken());
		multiple = a * b;

		// 나누는 값이 작아야겠죠? 크다면 바꿔줍시다.
		if (a < b) {
			a = a ^ b;
			b = a ^ b;
			a = a ^ b;
		}

		while (b > 0) {
			mod = a % b;
			a = b;
			b = mod;
		}
		GCD = a;

		LCM = multiple / GCD;

		System.out.println(GCD);
		System.out.println(LCM);
```





















