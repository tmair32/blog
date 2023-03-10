---
title: "[6kyu] Playing with digits"
seoTitle: "Solving Codewars' Playing with Digits Problem"
seoDescription: "Here is a solution to the 6kyu-level Codewars problem "Playing with digits"."
datePublished: Fri Mar 10 2023 00:58:17 GMT+0000 (Coordinated Universal Time)
cuid: clf1tx149000209mj4jfeglt0
slug: playing-with-digits
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1678409545736/ce94f56c-8809-44da-903e-955ca6275af6.webp
tags: codewars, 6kyu

---

Please check at this [Link](https://www.codewars.com/kata/5552101f47fc5178b1000050/train/typescript)!

## Instructions

Some numbers have funny properties. For example:

> 89 --&gt; 8¹ + 9² = 89 \* 1

> 695 --&gt; 6² + 9³ + 5⁴= 1390 = 695 \* 2

> 46288 --&gt; 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 \* 51

Given a positive integer n written as abcd... (a, b, c, d... being digits) and a positive integer p

* we want to find a positive integer k, if it exists, such that the sum of the digits of n taken to the successive powers of p is equal to k \* n.
    

In other words:

> Is there an integer k such as : (a ^ p + b ^ (p+1) + c ^(p+2) + d ^ (p+3) + ...) = n \* k

If it is the case we will return k, if not return -1.

**Note**: n and p will always be given as strictly positive integers.

```typescript
dig_pow(89, 1) should return 1 since 8¹ + 9² = 89 = 89 * 1
dig_pow(92, 1) should return -1 since there is no k such as 9¹ + 2² equals 92 * k
dig_pow(695, 2) should return 2 since 6² + 9³ + 5⁴= 1390 = 695 * 2
dig_pow(46288, 3) should return 51 since 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51
```

---

## My solution method

```typescript
export class G964 {
    public static digPow = (n: number, p: number) => {
      const strN:string = String(n);
      let sum = 0;
      for (let i=0; i<strN.length; i++) {
        sum += parseInt(strN[i]) ** (i+p)
      }
      return sum % n === 0 ? Math.floor(sum / n) : -1;
    }
}
```