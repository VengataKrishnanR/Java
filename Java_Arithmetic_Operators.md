# Java Arithmetic Operators — Quick‑Glance Revision

> **Purpose:** Perform basic mathematical operations on numeric data types.  
> **Works On:** All numeric primitive types (`byte`, `short`, `char`, `int`, `long`, `float`, `double`).  
> **boolean** is **not** allowed in arithmetic operations.

---

## 1) List of Arithmetic Operators

| Operator | Operation         | Example      | Description |
|----------|-------------------|--------------|-------------|
| `+`      | Addition          | `a + b`      | Adds values (numeric) or concatenates if one operand is a `String` |
| `-`      | Subtraction       | `a - b`      | Subtracts second operand from first |
| `*`      | Multiplication    | `a * b`      | Multiplies values |
| `/`      | Division          | `a / b`      | Divides first by second (integer division truncates result) |
| `%`      | Modulus (Remainder)| `a % b`     | Remainder after division |

---

## 2) Examples

```java
int a = 10, b = 3;
System.out.println(a + b); // 13
System.out.println(a - b); // 7
System.out.println(a * b); // 30
System.out.println(a / b); // 3 (integer division)
System.out.println(a % b); // 1 (remainder)
```

---

## 3) Type Promotion in Arithmetic
- `byte`, `short`, `char` are **promoted to int** before operation.
```java
byte x = 5, y = 10;
byte z = (byte)(x + y); // x+y is int, needs cast
```
- If operands are different types, result type is **the wider type**.
```java
int i = 5; double d = 2.5;
double res = i + d; // result is double
```

---

## 4) Integer Division & Modulus
- Integer division **truncates** towards zero.
```java
System.out.println(7 / 2);   // 3
System.out.println(-7 / 2);  // -3
```
- Modulus keeps the **sign of the dividend**.
```java
System.out.println(7 % 2);   // 1
System.out.println(-7 % 2);  // -1
```

---

## 5) Floating‑Point Division & Modulus
- Division retains fraction.
```java
System.out.println(7.0 / 2); // 3.5
```
- `%` works with floating-point too.
```java
System.out.println(7.5 % 2.0); // 1.5
```

---

## 6) Special Cases: Infinity & NaN
```java
System.out.println(5.0 / 0);    // Infinity
System.out.println(-5.0 / 0);   // -Infinity
System.out.println(0.0 / 0.0);  // NaN
```

---

## 7) Overflow & Underflow
- No error on overflow; wraps around.
```java
int big = Integer.MAX_VALUE;
System.out.println(big + 1); // -2147483648
```

---

## 8) String + Number
- `+` acts as concatenation if **either operand** is a `String`.
```java
System.out.println("Sum: " + 5 + 3); // "Sum: 53"
System.out.println(5 + 3 + " Sum"); // "8 Sum"
```

---

## 9) Unary Plus & Minus
- `+` has no effect (identity).
- `-` negates value.
```java
int n = 5;
System.out.println(+n); // 5
System.out.println(-n); // -5
```

---

## 10) Compound Assignment Operators
| Operator | Example  | Equivalent to |
|----------|----------|---------------|
| `+=`     | `a += b` | `a = a + b`   |
| `-=`     | `a -= b` | `a = a - b`   |
| `*=`     | `a *= b` | `a = a * b`   |
| `/=`     | `a /= b` | `a = a / b`   |
| `%=`     | `a %= b` | `a = a % b`   |

- Implicit cast back to original type (avoids explicit cast for small types).
```java
byte b = 5;
b += 3; // OK
// b = b + 3; // ERROR: requires cast
```

---

## 11) Increment & Decrement
| Operator | Meaning      | Example | Notes |
|----------|--------------|---------|-------|
| `++a`    | Pre-increment| Add 1, then use value | Changes before use |
| `a++`    | Post-increment| Use value, then add 1 | Changes after use |
| `--a`    | Pre-decrement| Subtract 1, then use value | |
| `a--`    | Post-decrement| Use value, then subtract 1 | |

```java
int x = 5;
System.out.println(++x); // 6
System.out.println(x++); // 6 (then x=7)
```

---

## 12) Best Practices
- Use integer division only when truncation is intended.
- For monetary values, use `BigDecimal` for accuracy.
- Beware of overflow when multiplying large numbers.
- Be explicit with types to avoid unintended promotions.

---

## 13) Quick Reference Table

| Expression  | Result     | Type    |
|-------------|-----------|---------|
| `5 + 3`     | 8         | int     |
| `5 / 2`     | 2         | int     |
| `5 / 2.0`   | 2.5       | double  |
| `7 % 3`     | 1         | int     |
| `-7 % 3`    | -1        | int     |
| `5 + "A"`   | "5A"      | String  |

---

## 14) Quick Exercises
1. Output?
```java
System.out.println(10 / 4);
System.out.println(10 / 4.0);
System.out.println(7 % -3);
System.out.println("Java" + 1 + 2);
System.out.println(1 + 2 + "Java");
```
2. Why does `byte b = 5; b = b + 1;` fail but `b += 1;` works?

---

**Answers:**
1. `2`, `2.5`, `1`, `"Java12"`, `"3Java"`  
2. `b+1` promotes to int, needs explicit cast. `+=` includes implicit cast.

---
