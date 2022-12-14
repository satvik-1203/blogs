---
name: heap-and-stack
---

# What Is Stack And Heap Memory?

The computer stores memory in 2 ways, allocating memory in the Heap or Stack.
Before we dive deep into understanding both of them, Let me break it into small pieces.

> Stack Memory is basically used for data types that have predefined size given by the language.

> Heap Memory is the memory we allocate and free manually and size of it is unknown at compile time.

Lets dive deeper...

## Stack Memory

Stack Memory is based on the scope of call stack. Suppose you have a fresh call stack, and you define a variable `x = 10;` . Since this variable size is known as compile time,
the language will assign the variable in the stack memory.

When data is stored in the stack memory, the variables that refer to it have direct access to them.

```JS
var x = 10;

// In the call stack the rough representation would be
x = 10;
```

But the idea of Heap Memory is different.

## What is Heap Memory?

When variables don't have defined size at compile time, that data is stored in heap and variables hold the reference location in the Heap.

Suppose we initialize a new array to x. This is how the compiler would allocate memory. since array doesn't have fixed size at compile time.

```JS
var x =  xf013114;

var y = x;

y =  xf013114;
// y would hold the value xf013114 and hence editing y would also result in editing x cuz they hold same memory reference location.

// In the call stack the rough representation would be
x = xf013114;

// In the Heap memory the rough representation would be
xf013114 = [];

```

Usually initializing variables require us to use `new` keyword. This should give you a better understanding of what goes into Stack or Heap memory.

Initializing an array requires us to use `new` keyword, so we can say that arrays are stored in the heap.
if you observed carefully, when you initialize a variable `x to an array` , and then initialize `y to x`. `Editing values in y` would also be shown in x.

```JS
var a  = new Array(); // a = xf012113
var b = a; // b = xf012113

b.add(10); // editing the array in the location xf012113

print(a);
// [10];

// We get 10 in the console while printing a since a and b are pointing towards same location.

```
