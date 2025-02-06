[TOC]

# ICAST: Integral division result cast to double or float (ICAST_IDIV_CAST_TO_DOUBLE)
This code casts the result of an integral division (e.g., int or long division) operation to double or float. Doing division on integers truncates the result to the integer value closest to zero. The fact that the result was cast to double suggests that this precision should have been retained. What was probably meant was to cast one or both of the operands to double before performing the division. Here is an example:
```java
int x = 2;
int y = 5;
// Wrong: yields result 0.0
double value1 =  x / y;

// Right: yields result 0.4
double value2 =  x / (double) y;
```