# java-practic
# ☕ Java Mastery & Algorithms

This repository serves as a comprehensive collection of my Java programming journey, covering everything from core fundamentals to advanced multi-threaded systems and algorithmic analysis.

---

## 📂 Project Structure

```
├── Basic_Logic/          # Loops, Conditionals, and Patterns
├── OOPs_Concepts/        # Classes, Interfaces, and Inheritance
├── Multithreading/       # Concurrency, Synchronization, and Deadlocks
├── DAA_Algorithms/       # Master Method, Sorting, and Searching
└── README.md
```

---

## 📁 Module 1 — Basic Logic

> Covers fundamental programming constructs: loops, conditionals, and pattern printing.

---

###  1.1 Loops

#### For Loop
```java
public class ForLoopExample {
    public static void main(String[] args) {
        // Print numbers 1 to 10
        for (int i = 1; i <= 10; i++) {
            System.out.println("Number: " + i);
        }
    }
}
```

#### While Loop
```java
public class WhileLoopExample {
    public static void main(String[] args) {
        int i = 1;
        while (i <= 5) {
            System.out.println("Count: " + i);
            i++;
        }
    }
}
```

#### Do-While Loop
```java
public class DoWhileExample {
    public static void main(String[] args) {
        int i = 1;
        do {
            System.out.println("Value: " + i);
            i++;
        } while (i <= 5);
    }
}
```

---

###  1.2 Conditionals

#### If-Else
```java
public class IfElseExample {
    public static void main(String[] args) {
        int number = 42;

        if (number > 0) {
            System.out.println(number + " is Positive");
        } else if (number < 0) {
            System.out.println(number + " is Negative");
        } else {
            System.out.println("Number is Zero");
        }
    }
}
```

#### Switch Statement
```java
public class SwitchExample {
    public static void main(String[] args) {
        int day = 3;

        switch (day) {
            case 1: System.out.println("Monday");    break;
            case 2: System.out.println("Tuesday");   break;
            case 3: System.out.println("Wednesday"); break;
            case 4: System.out.println("Thursday");  break;
            case 5: System.out.println("Friday");    break;
            default: System.out.println("Weekend");
        }
    }
}
```

---

### 🔢 1.3 Pattern Printing

#### Right-Angled Star Triangle
```java
public class StarPattern {
    public static void main(String[] args) {
        int n = 5;
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```
**Output:**
```
* 
* * 
* * * 
* * * * 
* * * * * 
```

#### Number Pyramid
```java
public class NumberPattern {
    public static void main(String[] args) {
        int n = 5;
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print(j + " ");
            }
            System.out.println();
        }
    }
}
```
**Output:**
```
1 
1 2 
1 2 3 
1 2 3 4 
1 2 3 4 5 
```

#### Inverted Triangle
```java
public class InvertedPattern {
    public static void main(String[] args) {
        int n = 5;
        for (int i = n; i >= 1; i--) {
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```
**Output:**
```
* * * * * 
* * * * 
* * * 
* * 
* 
```

---

## 📁 Module 2 — OOPs Concepts

> Covers the four pillars of Object-Oriented Programming in Java.

---

### 🧱 2.1 Encapsulation

> Wrapping data (fields) and methods together, and restricting direct access using access modifiers.

```java
// BankAccount.java
public class BankAccount {
    private String owner;
    private double balance;  // private — cannot be accessed directly

    public BankAccount(String owner, double initialBalance) {
        this.owner = owner;
        this.balance = initialBalance;
    }

    // Getter
    public double getBalance() {
        return balance;
    }

    // Controlled Setter
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: Rs." + amount);
        } else {
            System.out.println("Invalid deposit amount.");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawn: Rs." + amount);
        } else {
            System.out.println("Insufficient balance.");
        }
    }
}

// Main.java
public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount("Ankur", 5000);
        account.deposit(1500);
        account.withdraw(2000);
        System.out.println("Balance: Rs." + account.getBalance());
    }
}
```
**Output:**
```
Deposited: Rs.1500.0
Withdrawn: Rs.2000.0
Balance: Rs.4500.0
```

---

### 🧬 2.2 Inheritance

> A child class acquires properties and behaviors of a parent class using the `extends` keyword.

```java
// Animal.java — Parent Class
public class Animal {
    String name;

    public Animal(String name) {
        this.name = name;
    }

    public void eat() {
        System.out.println(name + " is eating.");
    }

    public void sleep() {
        System.out.println(name + " is sleeping.");
    }
}

// Dog.java — Child Class
public class Dog extends Animal {

    public Dog(String name) {
        super(name);  // calls Animal constructor
    }

    public void bark() {
        System.out.println(name + " is barking!");
    }
}

// Main.java
public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog("Bruno");
        dog.eat();    // inherited from Animal
        dog.sleep();  // inherited from Animal
        dog.bark();   // Dog's own method
    }
}
```
**Output:**
```
Bruno is eating.
Bruno is sleeping.
Bruno is barking!
```

---

### 🎭 2.3 Polymorphism

#### Method Overloading (Compile-time Polymorphism)
```java
public class Calculator {

    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }

    public int add(int a, int b, int c) {
        return a + b + c;
    }

    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println("Int Add:    " + calc.add(5, 10));
        System.out.println("Double Add: " + calc.add(3.5, 2.5));
        System.out.println("Three Add:  " + calc.add(1, 2, 3));
    }
}
```
**Output:**
```
Int Add:    15
Double Add: 6.0
Three Add:  6
```

#### Method Overriding (Runtime Polymorphism)
```java
// Shape.java
public class Shape {
    public void draw() {
        System.out.println("Drawing a generic Shape");
    }
}

// Circle.java
public class Circle extends Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a Circle");
    }
}

// Rectangle.java
public class Rectangle extends Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a Rectangle");
    }
}

// Main.java
public class Main {
    public static void main(String[] args) {
        Shape s1 = new Circle();       // Runtime polymorphism
        Shape s2 = new Rectangle();

        s1.draw();
        s2.draw();
    }
}
```
**Output:**
```
Drawing a Circle
Drawing a Rectangle
```

---

### 🎨 2.4 Abstraction

#### Using Abstract Class
```java
// Vehicle.java — Abstract Class
public abstract class Vehicle {
    String brand;

    public Vehicle(String brand) {
        this.brand = brand;
    }

    // Abstract method — must be implemented by subclass
    public abstract void fuelType();

    // Concrete method — shared behavior
    public void start() {
        System.out.println(brand + " is starting...");
    }
}

// Car.java
public class Car extends Vehicle {
    public Car(String brand) {
        super(brand);
    }

    @Override
    public void fuelType() {
        System.out.println(brand + " runs on Petrol");
    }
}

// ElectricBike.java
public class ElectricBike extends Vehicle {
    public ElectricBike(String brand) {
        super(brand);
    }

    @Override
    public void fuelType() {
        System.out.println(brand + " runs on Electricity");
    }
}

// Main.java
public class Main {
    public static void main(String[] args) {
        Vehicle car  = new Car("Toyota");
        Vehicle bike = new ElectricBike("Ather");

        car.start();
        car.fuelType();

        bike.start();
        bike.fuelType();
    }
}
```
**Output:**
```
Toyota is starting...
Toyota runs on Petrol
Ather is starting...
Ather runs on Electricity
```

#### Using Interface
```java
// Printable.java
public interface Printable {
    void print();  // abstract by default
}

// Scannable.java
public interface Scannable {
    void scan();
}

// Printer.java — implements multiple interfaces
public class Printer implements Printable, Scannable {

    @Override
    public void print() {
        System.out.println("Printing document...");
    }

    @Override
    public void scan() {
        System.out.println("Scanning document...");
    }
}

// Main.java
public class Main {
    public static void main(String[] args) {
        Printer p = new Printer();
        p.print();
        p.scan();
    }
}
```
**Output:**
```
Printing document...
Scanning document...
```

---

### 2.5 Exception Handling

```java
// Custom Exception
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}

public class ExceptionDemo {

    static void withdraw(double balance, double amount)
            throws InsufficientFundsException {
        if (amount > balance) {
            throw new InsufficientFundsException(
                "Cannot withdraw Rs." + amount + ". Available: Rs." + balance
            );
        }
        System.out.println("Withdrawal successful: Rs." + amount);
    }

    public static void main(String[] args) {
        try {
            withdraw(3000, 5000);  // This will throw exception
        } catch (InsufficientFundsException e) {
            System.out.println("Exception caught: " + e.getMessage());
        } finally {
            System.out.println("Transaction process completed.");
        }
    }
}
```
**Output:**
```
Exception caught: Cannot withdraw Rs.5000.0. Available: Rs.3000.0
Transaction process completed.
```

---

## 🛠️ Requirements

- JDK 17 or higher *(recommended for modern Java features)*
- IDE: IntelliJ IDEA, Eclipse, or VS Code with Java Extension Pack
- Build Tool: Maven or Gradle *(optional)*

---

## 📌 Installation & Usage

1. **Clone the repository:**
```bash
git clone https://github.com/ankurfsdv-arch/java.git
```

2. **Navigate to a specific module:**
```bash
cd java/OOPs_Concepts
```

3. **Compile and run:**
```bash
javac Main.java
java Main
```

---

## 👨‍💻 Connect with Me

- **Developer:** Ankur Yadav — [GitHub Profile](https://github.com/ankurfsdv-arch)
- **Email:** ankurcse437@gmail.com
- **Portfolio:** [ankuryadav.vercel.app](https://ankuryadav.vercel.app)
