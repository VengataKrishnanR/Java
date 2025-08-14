
# Java Overview — Fundamentals, JVM/JRE/JDK, and First Program

## 1. What is Java?
- **Java** is a **platform-independent**, **object-oriented programming language**.
- Follows OOP principles: **Inheritance, Polymorphism, Encapsulation, Abstraction**.
- Highly popular due to its **portability**.

**Portability Motto — WORA (Write Once, Run Anywhere):**
- Write Java code once → Compile to **bytecode** → Run on any machine with a compatible JVM.
- Example: Code written on mobile can run on Linux, Windows, Mac — any system with JVM.

---

## 2. How Java Achieves Portability
### Compilation Flow
```
Java Source (.java) → Compiler (javac) → Bytecode (.class) → JVM → Machine Code → CPU
```
- **Java Source Code** → Compiled to **bytecode** by `javac`.
- **Bytecode** → Read by **JVM** → Converted to machine code → Executed by CPU.

---

## 3. JVM (Java Virtual Machine)
- **Abstract machine** (software, not physical).
- **Platform-dependent**: A JVM build is specific to the operating system.
- **Input:** Bytecode (.class)  
  **Output:** Machine code
- **JIT Compiler (Just-In-Time):** Converts bytecode to native code at runtime for performance.

**Why JVM makes Java portable:**
- Any JVM can interpret bytecode, regardless of where the bytecode was generated.

---

## 4. JRE (Java Runtime Environment)
- Includes:
  1. **JVM**
  2. **Class Libraries** (pre-written Java APIs like `java.lang`, `java.util`)
- Allows running Java programs, but not compiling them.
- **If you have JRE**: You can run any compiled Java bytecode.

---

## 5. JDK (Java Development Kit)
- Includes:
  - **JRE** (JVM + Class Libraries)
  - **Compiler (`javac`)**
  - **Debugger**
  - **Java Programming Language tools**
- Needed for **developing and compiling** Java code.
- **If you have JDK**: You can write, compile, and run Java programs.

---

## 6. Relationship Diagram
```
JDK = JRE + Compiler + Debugger + Language Tools
JRE = JVM + Class Libraries
JVM = Executes Bytecode
```

---

## 7. Java Editions
| Edition | Name | Purpose |
|---------|------|---------|
| **JSE** | Java Standard Edition | Core Java (OOP, libraries, multithreading, etc.) |
| **JEE** | Java Enterprise Edition | Core Java + enterprise APIs (Servlets, JSP, Transactions, Persistence APIs) |
| **JME** | Java Micro Edition (Jakarta EE) | APIs for mobile/embedded applications |

---

## 8. First Java Program

**Source Code (`Employee.java`):**
```java
public class Employee {
    public static void main(String[] args) {
        int a = -10;
        System.out.println("This is my first program");
        System.out.println("Output of a is " + a);
    }
}
```

### Structure Explanation
- **Class Name** = File Name (`Employee`)
- **`public static void main(String[] args)`**
  - **public**: Accessible by JVM from anywhere.
  - **static**: JVM can call without creating an object.
  - **void**: No return value.
  - **main**: Entry point of Java application.
  - **String[] args**: Accepts command-line arguments.
- **Comments:**
  - Single-line: `// comment`
  - Multi-line: `/* comment */`

---

## 9. Compilation and Execution
```bash
javac Employee.java   # Compiles source → Employee.class (bytecode)
java Employee         # Runs bytecode → Output shown in console
```

**Note:** If `.java` changes, recompile before running — JVM reads only updated `.class` files.

---

## 10. Key Takeaways
- **Java Program**: Platform-independent (runs anywhere with JVM).
- **JVM**: Platform-dependent (OS-specific).
- **JRE**: Runs Java programs (JVM + Libraries).
- **JDK**: Develops and runs Java programs (JRE + compiler + tools).


