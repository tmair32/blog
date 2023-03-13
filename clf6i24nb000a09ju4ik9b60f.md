---
title: "[6kyu] Does my number look big in this?"
seoTitle: "Solving Codewars' Does my number look big in this?"
seoDescription: "Here is a solution to the 6kyu-level Codewars problem "Does my number look big in this?"."
datePublished: Mon Mar 13 2023 07:25:10 GMT+0000 (Coordinated Universal Time)
cuid: clf6i24nb000a09ju4ik9b60f
slug: does-my-number-look-big-in-this
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678692234309/5f582c4e-08a9-42e8-9a93-7a5232f5942f.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1678692266812/39a4fa50-157d-4dd6-9624-71aa63031dd0.webp
tags: algorithms, javascript, typescript, codewars, 6kyu

---

## Instructions

A [**Narcissistic Number**](https://en.wikipedia.org/wiki/Narcissistic_number) (or Armstrong Number) is a positive number which is the sum of its own digits, each raised to the power of the number of digits in a given base. In this Kata, we will restrict ourselves to decimal (base 10).

For example, take 153 (3 digits), which is narcissistic:

```typescript
1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153
```

and 1652 (4 digits), which isn't:

```typescript
1^4 + 6^4 + 5^4 + 2^4 = 1 + 1296 + 625 + 16 = 1938
```

The Challenge:

Your code must return **true** or **false** (not 'true' and 'false') depending upon whether the given number is a Narcissistic number in base 10.

This may be **True** and **False** in your language, e.g. PHP.

Error checking for text strings or other invalid inputs is not required, only valid positive non-zero integers will be passed into the function.

---

## My solution

```typescript
export function narcissistic(value: number): boolean {
  const strN = String(value)
  return strN.split('').reduce((res:number, acc:string) => {
    res += parseInt(acc) ** strN.length
    return res
  }, 0) === value
}
```

Please check this problem at this [Link](https://www.codewars.com/kata/5287e858c6b5a9678200083c/train/typescript)!