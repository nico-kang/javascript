Do splice and slice change the original array? How to delete the last element of an array?

splice() and slice() are both methods of JavaScript arrays, but they work differently.

The splice() method can add, remove, or replace elements in an array and return the deleted element. It modifiies the original array.

The slice() method creates a new array with elements from the original array, specified by start and end positions, without changing the original array.

Therefore, using the splice() method may change the original array, while the slice() method does not.

To delete the last element of an array, there are several ways:

To delete the last element of an array, use the pop() method to delete and return the last element:
const arr = [1, 2, 3, 4];
const lastElement = arr.pop();

Delete the last element of an array using the splice() method:
const arr = [1, 2, 3, 4];
arr.splice(-1, 1);

Use the slice() method and the spread operator (...) to create a new array containing all the elements except the last one:
const arr = [1, 2, 3, 4];
const newArr = [...arr.slice(0, -1)];
console.log(newArr); // [1, 2, 3]

It should be noted that all the above methods either change the original array or create a new one, without preserving the last element in the original array. If you want to retrieve only the last element, you can use indexing or the array method slice():