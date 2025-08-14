
# Java Variables — Part 2: Reference Data Types, Wrapper Classes, and Constants

## 1. Overview
This section covers **non-primitive data types** (reference types), **wrapper classes**, **autoboxing/unboxing**, and **constant variables** in Java.

Java data types are of two types:
1. **Primitive Data Types** — store actual values directly (e.g., `int`, `float`)
2. **Reference (Non-Primitive) Data Types** — store references (memory addresses) pointing to objects in the heap.

---

## 2. Reference Data Types

Reference data types store **memory addresses** that point to objects located in the **heap memory**.

### Key Examples of Reference Data Types
1. **Class**
2. **String**
3. **Interface**
4. **Array**

---

### 2.1 Class as a Reference Type
- When you create an object using `new`, space is allocated in the heap.
- The **variable name** holds a **reference** (address) to that heap memory.
- Example:
  ```java
  Employee emp = new Employee();
  ```
  - `emp` is a reference to the memory where the `Employee` object is stored.

**Memory Illustration:**
```
Heap Memory:
[Employee object | empId=10]

Reference Variable (Stack):
emp  ---> (address pointing to Employee object)
```

- Multiple variables can refer to the same object:
  ```java
  Employee emp2 = emp;
  ```
  Both `emp` and `emp2` point to the same object in memory.

---

### 2.2 String as a Reference Type
- Strings are **immutable**.
- Stored in a special memory region called the **String Constant Pool** (inside heap memory).
- **String literals** are reused to save memory.

**Example:**
```java
String s1 = "Hello";
String s2 = "Hello"; // points to the same literal in String Constant Pool
String s3 = new String("Hello"); // new object in heap (outside String Constant Pool)
```

**Behavior:**
- `==` checks if references point to the same memory location.
- `.equals()` checks if the content is the same.

**String Pool Behavior:**
```
Heap Memory:
[String Constant Pool]
   "Hello"  <-- s1, s2

[Heap outside SCP]
   "Hello" (new object) <-- s3
```

**Why Strings are Immutable:**
- Once created, string content cannot change.
- Any modification creates a **new** string object.

---

### 2.3 Interface as a Reference Type
- Cannot create an object of an interface.
- Can store **child class objects** in an interface reference.
```java
Person p = new Engineer();
Person t = new Teacher();
```
- This is valid because **parent references** can point to **child objects**.

---

### 2.4 Array as a Reference Type
- Arrays store multiple values of the same type in **contiguous memory**.
- The variable holds a reference to the array object in heap.

**1D Array Example:**
```java
int[] arr = new int[5];
arr[0] = 10;
arr[3] = 40;
```
**2D Array Example:**
```java
int[][] matrix = new int[5][4]; // 5 rows, 4 columns
matrix[2][2] = 20;
```

**Key Point:** Arrays are objects in Java, hence reference types.

---

## 3. Wrapper Classes

For each **primitive type**, Java provides a corresponding **wrapper class** (reference type).

| Primitive | Wrapper Class |
|-----------|--------------|
| byte      | Byte         |
| short     | Short        |
| int       | Integer      |
| long      | Long         |
| float     | Float        |
| double    | Double       |
| char      | Character    |
| boolean   | Boolean      |

**Why Wrapper Classes?**
1. Enable primitive types to be treated as objects.
2. Required for Java Collections (which only store objects).
3. Provide methods for type conversion and utility operations.
4. Allow passing primitives where **reference behavior** is needed.

---

### 3.1 Autoboxing
- Converting a **primitive** to its corresponding **wrapper class** automatically.
```java
int a = 10;
Integer obj = a; // autoboxing
```

### 3.2 Unboxing
- Converting a **wrapper object** back to a **primitive**.
```java
Integer obj = 20;
int b = obj; // unboxing
```

---

## 4. Constant Variables

A **constant variable** in Java is defined using `static final`.
- `static` → Single copy shared by all objects of the class.
- `final` → Value cannot be changed once assigned.

**Example:**
```java
public static final int EMPLOYEE_ID = 10;
```
- Naming convention: **UPPER_CASE_WITH_UNDERSCORES**
- Attempting to modify `EMPLOYEE_ID` will cause a compile-time error.

---

## 5. Summary Table

| Concept                  | Definition | Key Points |
|--------------------------|------------|------------|
| Reference Data Type      | Stores memory address of objects in heap | Class, String, Interface, Array |
| String Constant Pool     | Special heap area for string literals | Reuses literals, immutable |
| Wrapper Class            | Object representation of primitive type | Needed for Collections, methods |
| Autoboxing               | Primitive → Wrapper conversion | Automatic by compiler |
| Unboxing                 | Wrapper → Primitive conversion | Automatic by compiler |
| Constant Variable        | `static final` value | Immutable, shared across objects |

---
