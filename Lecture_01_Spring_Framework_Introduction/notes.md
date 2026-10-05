# 📘 Lecture 01 — Spring Framework (Introduction)

> 📺 **Source:** Coder Army — Spring Boot Series  
> 📅 **Date:** 29 September 2026

---

## 1. Core Java Recap

### Basic Java Program Structure:
```java
public class Main {
    public static void main(String[] args) {
        // your code here
    }
}
```

### Compilation Flow:
```
Main.java  →  javac  →  Main.class  →  JVM (Run)
 (Source)    (Compiler)  (Bytecode)    (Execution)
```

---

## 2. HTTP — The Rulebook of the Web

> **HTTP** (HyperText Transfer Protocol) is the rulebook for communication between a **client** and a **server**.  
> It is an **Application-layer protocol** that works on top of **TCP/IP**.

---

### 2.1 HTTP Methods

The first line of an HTTP request is called the **Request Line**.  
It contains the **method**, **path**, and **HTTP version**.

| Method | Action | Example |
|--------|--------|---------|
| **GET** | Read data | Fetch a list of orders |
| **POST** | Create data | Place a new order |
| **PUT** | Replace data completely | Update an entire profile |
| **PATCH** | Update data partially | Change only the phone number |
| **DELETE** | Remove data | Cancel an order |

---

### 2.2 HTTP Headers

Headers are **key-value pairs** that provide extra information about the request.

**Examples of what headers tell:**
- Who the client is
- What format the client can understand

---

### 2.3 HTTP Body

- The body carries the **actual data** sent by the client.
- It is commonly used with **POST**, **PUT**, and **PATCH** methods.
- In modern APIs, the request body is usually sent in **JSON format**.

---

### 2.4 HTTP Response

An HTTP Response consists of three parts:

```
HTTP Response
├── Status Code   (e.g., 200 OK)
├── Header        (metadata about the response)
└── Body          (actual data)
```

**Example:**
```
200 OK
Content-Type: Application/json

{
    "message": "login successfully"
}
```

---

## 3. Program Flow vs Website Flow

| Normal Program | Web Server |
|---------------|------------|
| Start | Start |
| Run | Run |
| Stop | Wait for Request |
| Exit | Give Response |
| — | Keep Running → **Loop** |

- A **normal program** runs once and then finishes (exits).
- A **server** keeps running continuously, waiting for requests.

```java
// Server conceptually works like this:
while (true) {
    // listen for request
    // send response
}
```

---

## 4. OOP Concepts Mapped to the HTTP World

| Core Java (OOP) | HTTP World |
|-----------------|------------|
| Object | HTTP Request |
| Classes | HTTP Response |
| Inheritance | URL |
| OOPs | Headers, Body |

---

## 5. Servlets

> A **Servlet** is a Java object that can handle HTTP requests.  
> In simple words, a Servlet is a **special Java class** designed for **web applications**.

### Conceptual Flow:
```
HTTP Request  →  Servlet  →  Java Code
```

- Servlets were the **first standard Java technology** created specifically for building web applications.
- A Servlet runs inside a **Servlet Container**.

---

### 5.1 Servlet Container

A Servlet Container sits **between the outside web world and your Java code**. It handles all the low-level web work for you.

**What a Servlet Container does:**
- Opening a port (such as `8080`)
- Listening for HTTP requests
- Reading TCP bytes
- Managing threads

**Examples of Servlet Containers:**
| # | Container |
|---|-----------|
| 1 | Apache Tomcat |
| 2 | Jetty |
| 3 | Undertow |

---

## 6. Need for Spring Framework

Servlets solved an important problem — they made it possible for Java applications to **handle HTTP requests properly**.

But building **large enterprise applications** directly with servlets became **difficult over time**.

### Common Problems with Servlets:
```
❌ Too much boilerplate code
❌ Too many configurations
```

### Enter Spring Framework:
- At this point, the **Spring Framework** was introduced.
- Spring helps us build Java applications in a **cleaner and more manageable way**.

---

## 7. Spring is an Ecosystem

- Spring is **not just one small library**.
- Spring is a **large ecosystem** of projects and frameworks.
- Different Spring projects solve **different problems**.

### Important Parts of the Spring Ecosystem:

| # | Project | Purpose |
|---|---------|---------|
| 1 | Spring Core | Foundation (IoC, DI, Beans) |
| 2 | Spring MVC | Web applications & REST APIs |
| 3 | Spring Data | Database access |
| 4 | Spring Security | Authentication & Authorization |
| 5 | Spring AOP | Aspect-Oriented Programming |
| 6 | Spring Boot | Rapid application development |
| 7 | Spring AI | AI integration |

---

## 8. Spring Core

> Spring Core is the **foundation** of the Spring ecosystem.

It provides the most basic and important features of Spring.

### Spring Core Includes:
```
IoC
Dependency Injection
Bean Management
Configuration
ApplicationContext
```

- Without Spring Core, **other Spring projects would not exist**.
- Spring Core is the **base** on which many other Spring modules are built.

---

## 9. Spring MVC

> Spring MVC is used to build **web applications** and **REST APIs**.

### Built on top of:
```
Servlets + Spring Core
```

- Spring MVC makes it easier to **handle web requests**.
- Instead of writing Servlet code directly, we can use **clean annotations** and **controller classes**.

### Example:
```java
@GetMapping("/hello")
public String sayHello() {
    return "Hello World";
}
```

---

## 10. Spring Data

Most applications need to **store data permanently**, which requires a **database**.

### 10.1 The JDBC Problem

Earlier, Java developers commonly used **JDBC**. With JDBC, developers had to:

```
Write SQL manually
Open database connections
Execute queries
Handle result sets
Close resources
Manage repetitive database code
```

### 10.2 Hibernate (ORM)

Later, frameworks like **Hibernate** made database work easier.

- Hibernate maps **Java objects to database tables**.
- This concept is called **Object-Relational Mapping (ORM)**.

### 10.3 JPA and Hibernate

**JPA** stands for **Java Persistence API**.

- JPA is a **specification** — it defines rules and guidelines for how Java objects should be mapped to database tables.
- But JPA itself does **not** provide the actual working implementation.
- **Hibernate** is one of the most popular **implementations** of JPA.

> In simple words:
> ```
> JPA tells what should be done.
> Hibernate actually does it.
> ```

---

## 📝 Key Takeaways

1. **HTTP** is the communication protocol between client and server (Application-layer, on top of TCP/IP)
2. **HTTP Methods** — GET (read), POST (create), PUT (replace), PATCH (update), DELETE (remove)
3. **HTTP Response** = Status Code + Headers + Body
4. A **server** runs continuously in a loop, unlike a normal program
5. **Servlets** were the first Java technology for web apps, but had too much boilerplate
6. **Spring Framework** was created to solve servlet complexity
7. **Spring is an Ecosystem** — Core, MVC, Data, Security, AOP, Boot, AI
8. **Spring Core** = Foundation (IoC, DI, Bean Management, ApplicationContext)
9. **Spring MVC** = Web layer built on top of Servlets + Spring Core
10. **Spring Data** = Database access; JDBC → Hibernate (ORM) → JPA (specification)
11. **JPA** tells what should be done, **Hibernate** actually does it

---

## 🔗 Resources

- [Spring Official Docs](https://docs.spring.io/spring-framework/reference/)
- [Coder Army YouTube](https://www.youtube.com/@CoderArmy9)

---

> 💡 **Next:** Send more pages to continue building these notes!
