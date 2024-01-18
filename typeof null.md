Why is the result of 'typeof null' an 'object'?

Kernel

The result of 'typeof null' being "object" is a legacy issue of the JavaScript language.

In the original version of JavaScript, a 32-bit value was used to represent a variable, with the first 3 bits representing the type of the value. 000 represents an object, 010 represents a floating point number, 100 represents a string, 110 represents a Boolean value, and other values are all considered pointers.

In this representation, null was interpreted as an all-zero pointer, that is, it is considered to be an empty object reference, so the result of typeof null is "object".

expand

Although this design is a legacy issue, it has become part of the JavaScript language for historical reasons and cannot be fixed. Therefore, it is recommended to use the strict equality operator (===) when determining whether a variable is null.