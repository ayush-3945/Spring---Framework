# 📘 Lecture 01 — Spring Framework (Introduction)

> 📺 **Source:** Coder Army — Spring Boot Series  
> 📅 **Date:** 29 September 2026

---

## 🤔 What is Spring Framework?

Spring Framework is an **open-source, lightweight Java framework** used to build enterprise-level applications.

- **Creator:** Rod Johnson (launched in 2003)
- **Purpose:** To simplify Java EE (Enterprise Edition) development
- **Core Idea:** "Don't reinvent the wheel" — eliminate boilerplate code and focus on business logic

---

## ❓ Why Spring Framework?

### Without Spring (Problems):
```
❌ Tight Coupling — Objects create their own dependencies
❌ Boilerplate Code — Too much repetitive code to write
❌ Hard to Test — Unit testing becomes difficult
❌ Hard to Maintain — One change = entire code change
```

### With Spring (Solutions):
```
✅ Loose Coupling — Spring manages objects via IoC
✅ Less Code — Annotations and auto-configuration reduce code
✅ Easy Testing — Dependency Injection makes testing simple
✅ Modular — Components are separated, easy to maintain
```

---

## 🏗️ Spring Framework Architecture

Spring Framework consists of multiple **modules** (layered architecture):

```
┌─────────────────────────────────────────────────┐
│                   Spring Framework               │
├─────────────────────────────────────────────────┤
│                                                  │
│  ┌─────────────┐  ┌──────────────┐              │
│  │  Spring Core │  │  Spring AOP  │              │
│  │  (IoC, DI)   │  │  (Aspects)   │              │
│  └─────────────┘  └──────────────┘              │
│                                                  │
│  ┌─────────────┐  ┌──────────────┐              │
│  │  Spring MVC  │  │  Spring Data │              │
│  │  (Web Layer) │  │  (Database)  │              │
│  └─────────────┘  └──────────────┘              │
│                                                  │
│  ┌─────────────┐  ┌──────────────┐              │
│  │  Spring      │  │  Spring      │              │
│  │  Security    │  │  Boot        │              │
│  └─────────────┘  └──────────────┘              │
│                                                  │
└─────────────────────────────────────────────────┘
```

---

## 🎯 Core Concepts of Spring Framework

### 1. IoC (Inversion of Control)

> "Hand over the control of object creation from the developer to the Spring container"

**Without IoC (Tight Coupling):**
```java
// Developer manually creates objects — TIGHT COUPLING ❌
class Car {
    private PetrolEngine engine = new PetrolEngine();  // hardcoded!
    
    void drive() {
        engine.start();
    }
}
// What if we need a DieselEngine? We'd have to change the entire code! 😩
```

**With IoC (Loose Coupling):**
```java
// Spring container manages objects — LOOSE COUPLING ✅
class Car {
    private Engine engine;  // use an interface
    
    // Spring will inject the correct engine automatically
    Car(Engine engine) {
        this.engine = engine;
    }
    
    void drive() {
        engine.start();
    }
}
// Now PetrolEngine or DieselEngine — Spring handles it! 😎
```

### 2. DI (Dependency Injection)

> "Inject dependencies from the outside, don't create them internally"

**3 Types of Dependency Injection:**

| Type | How | When to Use |
|------|-----|-------------|
| **Constructor Injection** | Via constructor | ✅ Recommended (immutable) |
| **Setter Injection** | Via setter method | Optional dependencies |
| **Field Injection** | `@Autowired` directly on field | ❌ Not recommended |

```java
// Constructor Injection (BEST ✅)
@Component
class Car {
    private final Engine engine;

    @Autowired
    public Car(Engine engine) {
        this.engine = engine;
    }
}

// Setter Injection
@Component
class Car {
    private Engine engine;

    @Autowired
    public void setEngine(Engine engine) {
        this.engine = engine;
    }
}

// Field Injection (AVOID ❌)
@Component
class Car {
    @Autowired
    private Engine engine;
}
```

### 3. Spring Container (ApplicationContext)

> Spring Container = the place where all **Beans** (objects) live and are managed

```java
// Starting the Spring Container
ApplicationContext context = new ClassPathXmlApplicationContext("config.xml");

// Or annotation-based:
ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);

// Retrieving a Bean from the container
Car car = context.getBean(Car.class);
car.drive();  // Spring has already injected the engine! ✅
```

### 4. Beans

> **Bean** = A Java object that is managed by the Spring Container

```java
// Use @Component to register a class as a Bean
@Component
public class PetrolEngine implements Engine {
    public void start() {
        System.out.println("Petrol Engine Started! 🚗");
    }
}
```

---

## 🔄 Spring vs Spring Boot

| Feature | Spring Framework | Spring Boot |
|---------|-----------------|-------------|
| Configuration | Manual (XML / Java) | Auto-configuration |
| Setup Time | Slow (lots of config) | Fast (starter dependencies) |
| Server | External (install Tomcat) | Embedded (built-in Tomcat) |
| Complexity | High | Low |
| Use Case | Fine-grained control | Rapid development |

> **Spring Boot = Spring Framework + Auto Configuration + Embedded Server**

---

## 📝 Key Takeaways

1. **Spring Framework** = The most popular Java framework
2. **IoC** = Hand over object creation control to Spring
3. **DI** = Inject dependencies from the outside
4. **Bean** = A Spring-managed object
5. **Spring Container** = Home of all Beans (ApplicationContext)
6. **Spring Boot** = Simplified version of Spring (auto-config + embedded server)

---

## 🔗 Resources

- [Spring Official Docs](https://docs.spring.io/spring-framework/reference/)
- [Coder Army YouTube](https://www.youtube.com/@CoderArmy9)

---

> 💡 **Next Topic:** Setting up first Spring Boot project using Spring Initializr
