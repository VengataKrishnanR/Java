# Type Casting & Type Promotion in Java

## 1. **Type Casting**
Type casting in Java is the process of converting a variable from one data type to another.

### **Types of Type Casting**
1. **Widening Casting (Implicit / Automatic Conversion)**
   - Converting a smaller type to a larger type size.
   - Performed automatically by Java (no data loss).
   - **Order:** byte → short → int → long → float → double
   - **Example:**
     ```java
     int num = 10;
     double d = num; // int to double
     ```

2. **Narrowing Casting (Explicit / Manual Conversion)**
   - Converting a larger type to a smaller type size.
   - Must be done manually using **(type)**.
   - Might lead to **data loss** or **precision loss**.
   - **Example:**
     ```java
     double d = 9.78;
     int num = (int) d; // double to int (fraction lost)
     ```

---

## 2. **Type Promotion in Expressions**
Type promotion is Java’s way of automatically converting operands to a common type while evaluating an expression.

### **Rules of Type Promotion**
1. **byte, short, char → int**  
   - In arithmetic operations, `byte`, `short`, and `char` are **promoted to int**.
   - **Example:**
     ```java
     byte a = 10, b = 20;
     byte c = a + b; // ERROR: a+b is promoted to int
     byte c = (byte) (a + b); // Correct
     ```

2. **If one operand is long → whole expression becomes long**
   ```java
   int a = 5;
   long b = 6;
   long result = a + b; // result is long
   ```

3. **If one operand is float → whole expression becomes float**
   ```java
   int a = 5;
   float b = 6.5f;
   float result = a + b; // result is float
   ```

4. **If one operand is double → whole expression becomes double**
   ```java
   int a = 5;
   double b = 6.5;
   double result = a + b; // result is double
   ```

5. **char is promoted to int in expressions**
   ```java
   char ch = 'A'; // Unicode 65
   int result = ch + 2; // 65 + 2 = 67
   ```

---

## 3. **Key Points to Remember**
- **Automatic Widening** happens when assigning smaller type to larger type.
- **Explicit Narrowing** required when converting larger type to smaller type.
- **byte, short, char** are always promoted to **int** in expressions.
- Mixed type expressions follow the **largest type** rule.
- Casting may **truncate values** or cause **overflow**.

---

## 4. **Quick Reference Table**

| From Type   | To Type (Widening) | Requires Casting? | Data Loss? |
|-------------|-------------------|-------------------|------------|
| byte        | short, int, long, float, double | No | No |
| short       | int, long, float, double | No | No |
| char        | int, long, float, double | No | No |
| int         | long, float, double | No | No |
| long        | float, double | No | Possible (precision) |
| float       | double | No | Possible (precision) |
| double      | float, long, int, short, byte, char | Yes | Yes |
| float       | long, int, short, byte, char | Yes | Yes |
| long        | int, short, byte, char | Yes | Yes |

---

## 5. **Example Summary**
```java
// Widening
int a = 10;
double d = a; // OK

// Narrowing
double x = 9.99;
int y = (int) x; // Fraction lost

// Promotion
byte b1 = 5, b2 = 6;
int result = b1 + b2; // Promoted to int

char ch = 'A'; // 65
int val = ch + 5; // 70
```
