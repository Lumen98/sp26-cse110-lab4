# Part 1:

### Question 1

Line 9 prints: values added:  20

The if block runs because add is true. Inside, result gets declared with var and set to num1 + num2, which is 10 + 10 = 20. Since var is function-scoped, result exists everywhere inside sumValues, so line 9 has no problem printing it as 20.

---

### Question 2

Line 13 prints: final result:  20

var doesn't care about block scope, it only cares about function scope. That means result doesn't disappear when the if block ends. It sticks around for the rest of sumValues, so by the time line 13 runs, result is still 20.

---

### Question 3

Using var is a bad idea for a few reasons:

1. **Variables escape their blocks**: If you declare a var inside an if block, you can still use it outside that block. That makes code confusing because where a variable "lives" doesn't match how the code looks.
2. **Hoisting is weird**: JavaScript moves var declarations to the top of the function behind the scenes. So the variable kind of exists before you actually wrote it, which can give you undefined instead of an error and hide bugs.
3. **You can declare the same variable twice**: var lets you re-declare a variable in the same scope without complaining. That can quietly overwrite values and cause bugs that are a pain to track down.

let and const fix all of this. They're block-scoped, won't let you re-declare in the same scope, and just behave the way you'd expect.

---

## let declaration

### Question 4

Line 9 prints: values added:  20

let is block-scoped, but line 9 still lives inside the if block, so result is fair game there. It got declared with let, started as 0, then got reassigned to 10 + 10 = 20. Line 9 prints it without any issues.

---

### Question 5

Line 13 throws a **ReferenceError**: result is not defined

let only exists inside the block it was declared in. Once the if block closes on line 11, result is basically gone. Line 13 sits outside that block, so trying to use result there crashes with a ReferenceError.

---

## const declaration

### Question 6

Line 9 never runs, a **TypeError** gets thrown on line 7: Assignment to constant variable

Once you declare something with const, you can't reassign it. Line 5 sets const result = 0, and then line 7 tries to give it a new value with result = num1 + num2. That's not allowed, so it throws a TypeError before the code ever makes it to line 9.

---

### Question 7

Line 13 never runs either, the TypeError from line 7 already crashed everything.

Even if the crash didn't happen, const is block-scoped just like let, so result wouldn't exist on line 13 anyway, that would throw a ReferenceError. But it doesn't matter because the program already died on line 7.
