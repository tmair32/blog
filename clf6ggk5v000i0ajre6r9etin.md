---
title: "[6ky] Stop gninnipS My sdroW!"
seoTitle: "Solving Codewars' Stop gninnipS My sdroW!"
seoDescription: "Here is a solution to the 6kyu-level Codewars problem "Stop gninnipS My sdroW!"."
datePublished: Mon Mar 13 2023 06:40:24 GMT+0000 (Coordinated Universal Time)
cuid: clf6ggk5v000i0ajre6r9etin
slug: stop-gninnips-my-sdrow
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678689518437/66ea8e11-965b-4efa-b8e8-48aeeae4d32d.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1678689431188/a44bfa94-169e-4940-bb56-8cde17556042.webp
tags: algorithms, javascript, typescript, codewars, 6kyu

---

## Instructions

Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed (Just like the name of this Kata). Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.

Examples:

```typescript
spinWords( "Hey fellow warriors" ) => returns "Hey wollef sroirraw" 
spinWords( "This is a test") => returns "This is a test" 
spinWords( "This is another test" )=> returns "This is rehtona test"
```

---

## My solution method

```typescript
export function spinWords(words: string): string {
  return words.split(' ').map((word: string) => {
    if (word.length >= 5) {
      return word.split('').reverse().join('')
    }
    return word
  }).join(' ')
}
```