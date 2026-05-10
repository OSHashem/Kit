# Java Tutorial - Day 1

## Anatomy of a Java Program
### Functions
The smallest building block of a Java program. A function performs a specific task and belongs to a class 

### The Main Method
Every Java program requires a main function; it acts as the entry point where execution begins.

### Classes
Used to organize code, similar to sections in a supermarket. The class containing the main method is typically named Main.

## Types and Variables

### Variables 
Stores data; Use the camelCase naming convention (e.g., myVariable)

## Primitive Types: Used for simple values 

### Whole Numbers
byte, short, int, and long. int is the default, while long requires an L suffix for large values.

### Decimals 
float and double for decimal numbers, with double being the default. Use an F suffix for float literals.
### Characters 
char for single characters.
### Booleans 
boolean for true/false values.

Example:

```java
byte age = 30; 
int viewsCount = 120000; 
double price = 10.99; 
boolean isEligible = true; 
char letter = 'A'; 
```

Note: Primitive Types are Independent;
If you assign one primitive variable to another, the value is copied. Changing one does not affect the other.

```java
int x = 1;
int y = x;
x = 2; (Result: y remains 1).
```

## Reference Types
Used for complex objects (e.g., Date). They store a reference to the actual data in memory, allowing for more complex data structures.

Example: 
```java
Date now = new Date(); 
```

Note: Reference Types share the same Object;
When you assign one reference variable to another, you are copying the address, not the object itself. Both variables now point to the exact same spot in memory.

```java
Point point1 = new Point(1, 1); 
Point point2 = point1; 
// If you update point1 (e.g., changing x to 2), that change will be visible when you access point2 because they reference the same object in memory 
```
## Memory Differences
A critical distinction between primitive and reference types is how they are managed in memory. Primitive variables are independent, while reference types hold a reference to a location in memory, meaning they can affect the original object when modified

