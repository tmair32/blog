---
title: "Make Object Oriented Types with Axios"
seoTitle: "Make Object Oriented Types with Axios"
seoDescription: "Learn how to implement object-oriented types in TypeScript with Axios while applying SOLID principles. Enhance your coding skills and build efficient."
datePublished: Tue Mar 14 2023 09:46:39 GMT+0000 (Coordinated Universal Time)
cuid: clf82jxl201p6xnnvdl0hc0yk
slug: make-object-oriented-types-with-axios
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1678776845952/d441a8d6-e1dc-421c-a702-c450bc61fbfe.png
tags: javascript, typescript, axios, object-oriented-programming, solid-principles

---

## Before Begining

I have been struggling over the past two days to figure out the best way to write code in TypeScript while adhering to the SOLID principles.

Specifically, I have been designing a class that uses Axios to communicate with a REST API.

I have been researching extensively to determine the most efficient, maintainable, and SOLID-compliant way to set up types for this class.

I do not necessarily believe that the approach I have come up with is the definitive answer, and I would be more than happy to receive feedback and suggestions if there are better ways to approach this problem.

Below are the code examples that I have developed after two days of contemplation. I would greatly appreciate it if you could take a look and offer any advice or guidance that you may have.

Thank you for your time and consideration.

## AxiosRepository

Start by creating an AxiosRepository class that will handle all the HTTP requests to our API. This `AxiosRepository` will have methods for all the CRUD operations.

```typescript
import axios, { AxiosResponse } from "axios";

interface Repository<T, K> {
  get(id: number): Promise<T>;
  getAll(): Promise<T[]>;
  create(data: K): Promise<T>;
  update(id: number, data: K): Promise<T>;
  delete(id: number): Promise<void>;
}

class AxiosRepository<T, K> implements Repository<T, K> {
  private readonly apiUrl: string;

  constructor(apiUrl: string) {
    this.apiUrl = apiUrl;
  }

  public async get(id: number): Promise<T> {
    const response: AxiosResponse<T> = await axios.get(`${this.apiUrl}/${id}`);
    return response.data;
  }

  public async getAll(): Promise<T[]> {
    const response: AxiosResponse<T[]> = await axios.get(this.apiUrl);
    return response.data;
  }

  public async create(data: K): Promise<T> {
    const response: AxiosResponse<T> = await axios.post(this.apiUrl, data);
    return response.data;
  }

  public async update(id: number, data: K): Promise<T> {
    const response: AxiosResponse<T> = await axios.put(`${this.apiUrl}/${id}`, data);
    return response.data;
  }

  public async delete(id: number): Promise<void> {
    await axios.delete(`${this.apiUrl}/${id}`);
  }
}
```

Each method returns a Promise with an AxiosResponse that holds the response data from the API.

## AxiosService

Next, create an AxiosService class that will use the AxiosRepository to perform CRUD operations on our data. This class will also apply SOLID principles by separating concerns and making the code more modular.

```typescript
export class AxiosService<T, K> implements Repository<T, K> {
  private readonly axiosRepository: AxiosRepository<T, K>;

  constructor(apiUrl: string) {
    this.axiosRepository = new AxiosRepository<T, K>(apiUrl);
  }

  public async get(id: number): Promise<T> {
    return await this.axiosRepository.get(id);
  }

  public async getAll(): Promise<T[]> {
    return await this.axiosRepository.getAll();
  }

  public async create(data: K): Promise<T> {
    return await this.axiosRepository.create(data);
  }

  public async update(id: number, data: K): Promise<T> {
    return await this.axiosRepository.update(id, data);
  }

  public async delete(id: number): Promise<void> {
    await this.axiosRepository.delete(id);
  }
}
```

Similarly, used the same `T` and `K` generic type parameters in the AxiosService class.

Now, let's see how our code conforms to the SOLID principles.

## SOLID Principles

SOLID is an acronym that stands for five design principles that were introduced by Robert C. Martin (also known as Uncle Bob). These principles help to create software that is easy to maintain, extend and modify. Let's see how your code adheres to each of these principles in my code:

1. ### Single Responsibility Principle (SRP)
    
    ```typescript
    export class AxiosRepository<T, K> {
      // HTTP requests implementation
    }
    
    export class AxiosService<T, K> {
      constructor(apiUrl: string) {
        this.axiosRepository = new AxiosRepository<T, K>(apiUrl);
      }
    
      // CRUD operations implementation
    }
    ```
    
    The `AxiosRepository` class has a single responsibility of handling HTTP requests to the API. It provides methods for all the CRUD operations and does not have any unnecessary responsibilities. Similarly, the `AxiosService` class has a single responsibility of performing CRUD operations on the data. It uses the `AxiosRepository` class to make HTTP requests and does not have any unnecessary responsibilities.
    
2. ### Open-Closed Principle (OCP)
    
    Our classes are open for extension but closed for modification. We can add new features to our codebase without modifying existing code. For example, if we need to add a new type of repository, we can create a new class that extends `AxiosRepository` or `Repository` and adds the additional functionality we need, without changing any of the existing code.
    

```typescript
export interface Repository<T, K> {
  get(id: number): Promise<T>;
  getAll(): Promise<T[]>;
  create(data: K): Promise<T>;
  update(id: number, data: K): Promise<T>;
  delete(id: number): Promise<void>;
}

export class AxiosRepository<T, K> implements Repository<T, K> {
  // Implementation of Repository methods using Axios
}

export class MongoRepository<T, K> extends AxiosRepository<T, K> {
  // Implementation of Repository methods using MongoDB
}

export class AxiosService<T, K> {
  constructor(repository: IRepository<T, K>) {
    this.repository = repository;
  }

  // CRUD operations implementation using IRepository methods
}
```

1. ### Liskov Substitution Principle (LSP)
    
    Since `AxiosRepository` and `AxiosService` both implement the same interface, they can be used interchangeably. This means that we can easily swap out one implementation for another without changing any of our existing code. This makes our code more flexible and easier to maintain.
    
2. ### Interface Segregation Principle (ISP)
    
    Our classes implement interfaces that define a specific set of methods for CRUD operations. This makes it easy to create new classes that implement the same interface and can be used interchangeably.
    
3. ### Dependency Inversion Principle (DIP)
    
    Our classes depend on abstractions instead of concrete implementations. This makes it easy to swap out the `axios` library with a different HTTP library if needed. Additionally, we can use dependency injection to inject the `AxiosRepository` and `AxiosService` classes into other classes that depend on them, making our code more modular and testable.
    

## Conclusion

I recently made some code based on SOLID principles, and while I am not an expert in OOP, I was able to do so after referencing various materials for two days.

However, I don't believe that this is the best possible code. Of course, it is possible to write even better code.

But this is my current limit, so I need your help. I aspire to become a better developer by continuously improving my code.

If you could improve my code, please leave a comment. I would greatly appreciate it.