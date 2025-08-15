# Java Relational Operators 

> **Purpose:** Compare two values and return a **boolean** (`true` / `false`).  
> **Usage:** Common in conditions, loops, and decision-making constructs.

---

## 1) List of Relational Operators

| Operator | Meaning                  | Works On                | Returns  |
|----------|--------------------------|-------------------------|----------|
| `==`     | Equal to                  | All primitives except boolean with different types (must be compatible) & object references | `boolean` |
| `!=`     | Not equal to              | Same as above           | `boolean` |
| `>`      | Greater than              | Numbers, `char`         | `boolean` |
| `<`      | Less than                 | Numbers, `char`         | `boolean` |
| `>=`     | Greater than or equal to  | Numbers, `char`         | `boolean` |
| `<=`     | Less than or equal to     | Numbers, `char`         | `boolean` |

> **Note:** For **boolean**, only `==` and `!=` are allowed.

---

## 2) Examples with Primitives

```java
int a = 5, b = 10;
System.out.println(a == b); // false
System.out.println(a != b); // true
System.out.println(a > b);  // false
System.out.println(a < b);  // true
System.out.println(a >= 5); // true
System.out.println(b <= 10);// true

char c1 = 'A', c2 = 'B';
System.out.println(c1 < c2); // true ('A'=65, 'B'=66)
```

---

## 3) Type Promotion in Relational Operators
- If operands are of different numeric types, **binary numeric promotion** applies:
  - `byte`, `short`, `char` → promoted to `int`
  - Then the **wider type** is chosen for comparison
```java
byte x = 5;
short y = 5;
System.out.println(x == y); // true (both promoted to int)
```

---

## 4) Comparing `boolean`
- Only `==` and `!=` allowed
```java
boolean flag1 = true, flag2 = false;
System.out.println(flag1 == flag2); // false
System.out.println(flag1 != flag2); // true
// flag1 > flag2; // ERROR
```

---

## 5) Comparing `char`
- Compared by **Unicode value**
```java
char ch1 = 'a'; // 97
char ch2 = 'b'; // 98
System.out.println(ch1 < ch2); // true
```

---

## 6) Comparing Floating‑Point Numbers
- Floating-point precision may cause unexpected results
```java
double d1 = 0.1 * 3;
System.out.println(d1 == 0.3); // might be false due to precision errors
```

---

## 7) Comparing Objects (`==` vs `.equals()`)
- **`==`** compares **references** (memory addresses)
- **`.equals()`** compares **contents** (if overridden in class)
```java
String s1 = new String("Hello");
String s2 = new String("Hello");
System.out.println(s1 == s2);      // false (different objects)
System.out.println(s1.equals(s2)); // true (same content)
```

---

## 8) Special Notes
- **NaN (Not a Number)**: Any relational comparison with `NaN` is `false` except `!=` which is `true`
```java
double nan = Double.NaN;
System.out.println(nan < 1);   // false
System.out.println(nan >= 1);  // false
System.out.println(nan == nan);// false
System.out.println(nan != nan);// true
```

- **Infinity**: Can be compared normally
```java
double posInf = Double.POSITIVE_INFINITY;
System.out.println(posInf > 1); // true
```

---

## 9) Best Practices
- For floating-point, avoid `==` for equality; use a tolerance (`epsilon`)
```java
double a = 0.3, b = 0.1 * 3;
System.out.println(Math.abs(a - b) < 1e-9); // true
```
- Use `.equals()` for object content comparison.
- Understand **type promotion** to avoid hidden surprises.

---

