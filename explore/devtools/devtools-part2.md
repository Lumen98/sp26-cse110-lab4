# DevTools Part 2

1. The bug was that num1 and num2 were strings, not numbers. When you grab values from input boxes using .value, they come in as strings. So when the code did num1 + num2, it just stuck them together instead of adding them. That's why 2 + 3 came out as 23 instead of 5. I could see this in the Watch panel where num1 was "2", num2 was "3", and typeof result was "string".

2. To fix it, I wrapped num1 and num2 with Number() so they get turned into actual numbers before being added. So I changed line 9 from:

   let result = num1 + num2;

   to:

   let result = Number(num1) + Number(num2);

   Now 2 + 3 actually gives 5.
