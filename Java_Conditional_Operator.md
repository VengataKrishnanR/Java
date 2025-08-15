# Java Conditional (Ternary) Operator — Quick‑Glance Revision

> **Purpose:** Shorthand for `if-else` that returns a value based on a condition.  
> **Syntax:**  
> ```java
> result = (condition) ? valueIfTrue : valueIfFalse;
> ```

---

## 1) Syntax Breakdown
- **condition** → boolean expression (`true` or `false`)
- **valueIfTrue** → returned if condition is `true`
- **valueIfFalse** → returned if condition is `false`

```java
int max = (a > b) ? a : b;
```

---

## 2) Key Rules
1. **Condition must be boolean** — no implicit int-to-boolean conversion like C/C++.
2. **Type compatibility**:
   - If both expressions are of the same type → result is that type.
   - If different types → **binary numeric promotion** or type inference rules apply.
3. Operator is **right-associative** — can be nested.

---

## 3) Examples with Primitives

```java
int a = 10, b = 20;
int max = (a > b) ? a : b; // 20

boolean isEven = (a % 2 == 0) ? true : false; // true
```

---

## 4) Type Promotion in Conditional Operator
### 4.1 Numeric Types
```java
byte x = 10;
byte y = 20;
var res = (true) ? x : y; // res is byte (same type)

int i = 5;
double d = 5.5;
var res2 = (i > 0) ? i : d; // res2 is double (promotion)
```

### 4.2 Reference Types
- If both arms are **reference types**, result type is the most specific common superclass or interface.

```java
Number n = (true) ? Integer.valueOf(5) : Double.valueOf(5.5); // Number
```

### 4.3 Null Handling
- If one arm is `null` and the other is a reference type → result is that reference type.
```java
String str = (true) ? null : "Hello"; // String
```

---

## 5) Nested Conditional Operators
```java
int a = 5, b = 10, c = 15;
int max = (a > b) ? a : (b > c) ? b : c;
// equivalent to: if(a>b) a; else if(b>c) b; else c;
```

> Be careful: Too much nesting reduces readability.

---

## 6) Conditional Operator vs if‑else
- **Use conditional operator** for simple expressions returning values.
- **Use if‑else** for multi-step logic or when statements (not just expressions) are needed.

```java
// Ternary
String result = (score >= 50) ? "Pass" : "Fail";

// if-else
if (score >= 50) {
    result = "Pass";
} else {
    result = "Fail";
}
```

---

## 7) Common Pitfalls
1. **Side effects in expressions** — avoid complex operations inside ternary arms.
```java
int val = (x > 0) ? x++ : --x; // changes x as a side-effect
```
2. **Type mismatches** — ensure arms are compatible or explicitly cast.
```java
// ERROR: incompatible types without casting
char c = (true) ? 65 : 'A'; // 65 is int literal
char c2 = (true) ? (char)65 : 'A'; // OK
```

---

## 8) Real-World Uses
- Value assignment with condition:
```java
String status = (age >= 18) ? "Adult" : "Minor";
```
- Inline decision in method arguments:
```java
System.out.println((n % 2 == 0) ? "Even" : "Odd");
```
- Default values:
```java
String name = (inputName != null) ? inputName : "Guest";
```

---

## 9) Quick Reference Table

| Example                                 | Output / Result | Reason |
|-----------------------------------------|-----------------|--------|
| `(5 > 3) ? 10 : 20`                     | 10              | True branch |
| `(5 < 3) ? 10 : 20`                     | 20              | False branch |
| `(true) ? "Yes" : "No"`                 | "Yes"           | True branch |
| `(false) ? 1.5 : 2`                     | 2.0             | Promotion to double |
| `(true) ? null : "Hello"`               | null            | null allowed |
| `(false) ? 65 : 'A'`                    | 'A'             | False branch, char chosen |

---

## 10) Quick Exercises
1. Output?
```java
int a = 3, b = 5;
System.out.println((a+b > 7) ? "High" : "Low");
System.out.println((true) ? 10 : 10.5);
System.out.println((false) ? 'B' : 66);
```
2. Why does `(true) ? 65 : 'A'` fail without casting to `char`?

---

**Answers:**
1. "High", 10.0 (promotion to double), 'B'  
2. Because `65` is an `int` literal, causing type mismatch with `char` without explicit cast.
b b 
