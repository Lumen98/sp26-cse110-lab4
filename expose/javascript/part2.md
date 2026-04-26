# Part 2:

### Question 1

Line 12 prints: 3

i gets declared with var inside the for loop on line 6. Since var is function-scoped, i sneaks out of the loop and is still around anywhere in discountPrices. After the loop goes through all 3 items in [100, 200, 300], i ends up as 3, that's the value that made i < prices.length false and kicked us out of the loop. So line 12 logs 3.

---

### Question 2

Line 13 prints: 150

discountedPrice gets declared with var inside the for loop on line 7. Because var is function-scoped, it escapes the loop and is still hanging around at line 13. On the last loop, prices[2] is 300, so discountedPrice = 300 * (1 - 0.5) = 150. That's whatever it's holding when the loop ends, so line 13 logs 150.

---

### Question 3

Line 14 prints: 150

finalPrice is declared with var on line 4 at the function level and starts at 0. It's function-scoped, so it's usable anywhere in discountPrices, including line 14. On the last iteration, finalPrice = Math.round(150 * 100) / 100 = 150. That value sticks around after the loop ends, so line 14 logs 150.

---

### Question 4

Returns: [50, 100, 150]

The function runs all the way through and returns the discounted array. Every loop, it grabs a price, multiplies it by (1 - 0.5) for the 50% off, rounds it to 2 decimal places, and pushes it onto discounted:
- 100 * 0.5 = 50
- 200 * 0.5 = 100
- 300 * 0.5 = 150

Everything's declared with var and is function-scoped, so nothing breaks and the function finishes fine.

---

### Question 5

Line 12 throws a **ReferenceError**: i is not defined

i is declared with let inside the for loop on line 6. let is block-scoped, so i only lives inside the loop's curly braces. Once the loop ends, i is gone for good. Line 12 is outside the loop, so trying to use i there crashes with a ReferenceError.

---

### Question 6

Line 13 throws a **ReferenceError**: discountedPrice is not defined

discountedPrice is declared with let on line 7, inside the for loop's block. let is block-scoped, so discountedPrice only exists inside that loop. Once the loop ends, it's gone. Line 13 is outside the loop, so trying to use discountedPrice there crashes with a ReferenceError.

---

### Question 7

Line 14 prints: 150

finalPrice is declared with let on line 4 at the **function level**, outside the loop. That means it's scoped to the entire discountPrices function and is still usable at line 14. After the last iteration, finalPrice holds Math.round(150 * 100) / 100 = 150, so line 14 logs 150.

---

### Question 8

Returns: [50, 100, 150]

The function finishes without breaking anything. discounted and finalPrice are declared with let at the function level, so they stick around the whole time. i and discountedPrice are block-scoped to the loop, but they don't need to be used outside it anyway. Each iteration pushes finalPrice onto discounted, and discounted gets returned on line 16.

---

### Question 9

Line 11 throws a **ReferenceError**: i is not defined

i is declared with let in the for loop on line 6, so it's block-scoped to the loop. Once the loop ends, i is gone. Line 11 is outside the loop, so trying to use i there crashes with a ReferenceError.

---

### Question 10

Line 12 prints: 3

length is declared with const on line 4 at the function level. It's scoped to the whole discountPrices function, so it's available at line 12. It got set to prices.length, which is 3 for the input [100, 200, 300]. const stops you from reassigning, but it doesn't change scope, so length is still usable outside the loop and logs 3.

---

### Question 11

Returns: [50, 100, 150]

The function runs through fine. discounted is declared with const at the function level. Even though const won't let you reassign a variable, it does **not** stop you from changing what's inside an array, discounted.push() just adds stuff to the existing array instead of reassigning the variable itself. Each iteration pushes the discounted price (50, 100, 150) onto discounted, which gets returned at the end.

---

### Question 12

Given the student object, here's how you'd access each thing:

**A.** Getting the value of the name property:
student.name or student['name']

**B.** Getting the value of the Grad Year property:
student['Grad Year']
You have to use bracket notation because the property name has a space in it, dot notation doesn't work for keys with spaces.

**C.** Calling the function for the greeting property:
student.greeting() or student['greeting']()
The parentheses are needed to actually run the function, not just point at it.

**D.** Getting the name property of the object inside Favorite Teacher:
student['Favorite Teacher'].name or student['Favorite Teacher']['name']
You need brackets for 'Favorite Teacher' because of the space, then either dot or bracket notation for the nested name.

**E.** Getting index zero from the courseLoad array:
student.courseLoad[0] or student['courseLoad'][0]
Grab the courseLoad property first, then use [0] to get the first item, which is 'CSE 110'.

---

### Question 13

**a.** '3' + 2 → '32'
The + operator with a string turns into string concatenation, so 2 gets turned into '2' and stuck onto '3'.

**b.** '3' - 2 → 1
The - operator doesn't do anything string-related, so '3' gets converted to the number 3, giving 3 - 2 = 1.

**c.** 3 + null → 3
null becomes 0 when used as a number, so 3 + 0 = 3.

**d.** '3' + null → '3null'
+ with a string means concatenation, so null gets turned into the string 'null'.

**e.** true + 3 → 4
true becomes 1 when used as a number, so 1 + 3 = 4.

**f.** false + null → 0
Both turn into numbers: false → 0, null → 0, so 0 + 0 = 0.

**g.** '3' + undefined → '3undefined'
+ with a string means concatenation, so undefined gets turned into the string 'undefined'.

**h.** '3' - undefined → NaN
'3' becomes 3, but undefined turns into NaN when used as a number, and any math with NaN spits out NaN.

---

### Question 14

**a.** '2' > 1 → true
'2' gets turned into the number 2, and 2 > 1 is true.

**b.** '2' < '12' → false
Both are strings, so they get compared character by character (like alphabetical order). The character '2' has a higher code than '1', so '2' counts as bigger, making this false.

**c.** 2 == '2' → true
The loose equality == turns '2' into the number 2, and 2 == 2 is true.

**d.** 2 === '2' → false
The strict equality === doesn't convert types. 2 is a number and '2' is a string, so they're not equal.

**e.** true == 2 → false
true becomes 1, and 1 == 2 is false.

**f.** true === Boolean(2) → true
Boolean(2) turns 2 into a boolean, any non-zero number becomes true. So you get true === true, which has the same type and value, so strict equality passes.

---

### Question 15

== is the **loose equality** operator, it converts types before comparing, forcing both values into the same type if they're different. === is the **strict equality** operator, it does **not** convert types and needs both the value AND the type to match to return true. For example, 2 == '2' is true because the string gets converted to a number, but 2 === '2' is false because a number and a string are never the same type. You should usually stick with === so you don't run into weird surprises from sneaky type conversions.

---

### Question 16

See part2-question16.js. The loop prints the value of a property if the property name starts with 'r' OR if the value is an odd number.

Output:
```
21
45
5
2
```
- redCars: 21, starts with 'r' AND is odd
- blueCars: 45, odd number
- raceCars: 5, starts with 'r' AND is odd
- rareCars: 2, starts with 'r'
- greenCars: 12, blackCars: 40, neither, so they get skipped

---

### Question 17

modifyArray([1,2,3], doSomething) returns [2, 4, 6].

modifyArray takes in an array and a callback function. It makes a new empty array called newArr, then loops through every item in the input array, calling callback(array[i]), which is really doSomething(array[i]), on each one and pushing the result into newArr:
- doSomething(1) → 1 * 2 = 2
- doSomething(2) → 2 * 2 = 4
- doSomething(3) → 3 * 2 = 6

newArr gets returned as [2, 4, 6].

---

### Question 18

See part2-question18.js. setInterval is used to call the time-printing function every 1000 milliseconds (1 second), forever. The new Date() is inside the callback so it grabs the current time every time it ticks instead of just once.

---

### Question 19

The output is:
```
1
4
3
2
```

JavaScript is single-threaded and uses something called the event loop. setTimeout callbacks always get pushed to a queue and run **after** the current synchronous code is done, even with a delay of 0. So here's what happens:
- 1 logs right away (regular synchronous code)
- Both setTimeouts get set up and put on hold
- 4 logs right away (regular synchronous code)
- Once the main code is done, the event loop checks the queue: 3 fires first (0ms delay), then 2 fires after 1000ms
