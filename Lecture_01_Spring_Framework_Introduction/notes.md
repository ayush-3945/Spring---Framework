# 📘 Lecture 01 — Spring Framework (Introduction)

> 📺 **Source:** Coder Army — Spring Boot Series  
> 📅 **Date:** 29 September 2026

---

## 🤔 What is Spring Framework?

Spring Framework ek **open-source, lightweight Java framework** hai jo enterprise-level applications banane ke liye use hota hai.

- **Creator:** Rod Johnson (2003 mein launch hua)
- **Purpose:** Java EE (Enterprise Edition) ko simple aur easy banana
- **Core Idea:** "Don't reinvent the wheel" — boilerplate code hatao, business logic pe focus karo

---

## ❓ Why Spring Framework?

### Without Spring (Problems):
```
❌ Tight Coupling — Objects apne dependencies khud create karte hain
❌ Boilerplate Code — Bahut zyada repetitive code likhna padta hai
❌ Hard to Test — Unit testing mushkil hoti hai
❌ Hard to Maintain — Ek change = pura code change
```

### With Spring (Solutions):
```
✅ Loose Coupling — Spring objects ko manage karta hai (IoC)
✅ Less Code — Annotations aur auto-configuration se kam code
✅ Easy Testing — Dependency Injection se testing easy
✅ Modular — Components alag-alag, easy to maintain
```

---

## 🏗️ Spring Framework Architecture

Spring Framework ke **modules** hain (layered architecture):

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

> "Object creation ka control developer se Spring container ko de do"

**Without IoC (Tight Coupling):**
```java
// Developer manually creates objects — TIGHT COUPLING ❌
class Car {
    private PetrolEngine engine = new PetrolEngine();  // hardcoded!
    
    void drive() {
        engine.start();
    }
}
// Agar DieselEngine chahiye toh? Pura code change karo! 😩
```

**With IoC (Loose Coupling):**
```java
// Spring container manages objects — LOOSE COUPLING ✅
class Car {
    private Engine engine;  // interface use karo
    
    // Spring will inject the correct engine automatically
    Car(Engine engine) {
        this.engine = engine;
    }
    
    void drive() {
        engine.start();
    }
}
// Ab PetrolEngine ya DieselEngine — Spring handle karega! 😎
```

### 2. DI (Dependency Injection)

> "Dependencies bahar se inject karo, andar se create mat karo"

**3 Types of Dependency Injection:**

| Type | How | When to Use |
|------|-----|-------------|
| **Constructor Injection** | Constructor ke through | ✅ Recommended (immutable) |
| **Setter Injection** | Setter method ke through | Optional dependencies |
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

> Spring Container = wo jagah jahan saare **Beans** (objects) rehte hain

```java
// Spring Container ko start karna
ApplicationContext context = new ClassPathXmlApplicationContext("config.xml");

// Ya annotation-based:
ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);

// Bean nikalna container se
Car car = context.getBean(Car.class);
car.drive();  // Spring ne engine inject kar diya hoga! ✅
```

### 4. Beans

> **Bean** = Wo Java object jo Spring Container manage karta hai

```java
// @Component se ek class ko Bean bana do
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
| Setup Time | Slow (bahut config) | Fast (starter dependencies) |
| Server | External (Tomcat install) | Embedded (built-in Tomcat) |
| Complexity | High | Low |
| Use Case | Fine-grained control | Rapid development |

> **Spring Boot = Spring Framework + Auto Configuration + Embedded Server**

---

## 📝 Key Takeaways

1. **Spring Framework** = Java ka sabse popular framework
2. **IoC** = Object creation ka control Spring ko de do
3. **DI** = Dependencies bahar se inject karo
4. **Bean** = Spring-managed object
5. **Spring Container** = Beans ka ghar (ApplicationContext)
6. **Spring Boot** = Spring ka easy version (auto-config + embedded server)

---

## 🔗 Resources

- [Spring Official Docs](https://docs.spring.io/spring-framework/reference/)
- [Coder Army YouTube](https://www.youtube.com/@CoderArmy9)

---

> 💡 **Next Topic:** Setting up first Spring Boot project using Spring Initializr
