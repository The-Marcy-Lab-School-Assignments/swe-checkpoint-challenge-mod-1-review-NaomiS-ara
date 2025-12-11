# Short Responses

For this assessment, aim to write a response with the following qualities:

- [ ] Addresses all parts of the prompt
- [ ] Accurately uses relevant technical terminology
- [ ] Is free of grammar and spelling mistakes
- [ ] Is easy to comprehend

For each prompt below, write your response in the space provided. Aim to answer each prompt in 2-5 concise sentences. Make sure to preview your markdown to check how it is rendered before submitting.

## Prompt 1

Consider the code below which has a bug. Instead of printing the correct letter grade, it always prints `"Your grade is: undefined"`.

```js
const getLetterGrade = (score) => {
  let letter;
  if (score >= 90) {
    let letter = "A";
  } else if (score >= 80) {
    let letter = "B";
  } else if (score >= 70) {
    let letter = "C";
  } else {
    let letter = "F";
  }

  return "Your grade is: " + letter;
};

console.log(getLetterGrade(95)); // This should print "Your grade is: A"
console.log(getLetterGrade(82)); // This should print "Your grade is: B"
console.log(getLetterGrade(74)); // This should print "Your grade is: C"
console.log(getLetterGrade(65)); // This should print "Your grade is: F"
```

**Part A**: Explain why this bug is occurring. Use proper technical terminology.

**Part B**: Then, explain how you would fix it.

### Response 1

**Part A:**

The bug is occuring because of the use of let inside each if/else block.
That second **let letter** creates a **new block-scoped variable** local to that **if block**, not the outer one.
So the inner **letter** variables exist only **inside** the `{ ... }` where they were created.
They do not update the outer **letter** variable.
Therefore, the outer **letter** remains **undefined** the whole time.
When you reach the return statement.
To simplify, This is a bug caused by shadowing a variable with a new one of the same name inside a block.

**Part B:**

The way i would go about fixing this bug is by removing the extra let inside the if statements that you assign the existing variable instead creating new useless ones.

---

## Prompt 2

Read the following code:

```js
const originalSettings = { volume: 50, brightness: 80 };
const newSettings = originalSettings;
newSettings.volume = 75;
console.log(originalSettings.volume);
```

**Part A:** What will be logged to the console? Why does this happen? Be sure to use precise technical terminology in your answer.

**Part B:** How would you modify the code so that changing `newSettings.volume` does NOT affect `originalSettings.volume`? Write the corrected code below your explanation.

### Response 2

**Part A:**

The console will log **75**. In javascript objects are reference types.
When you write:

```js
const newSettings = originalSettings;
```

You are not creating a new object.
Instead, you are copying the reference (memory address) to the same object.
That means **originalSettings** and **newSettings** both point to the exact same object in memory.
So when you do:
**newSettings.volume = 75;**
you are modifying the shared object, not just **newSettings**.
Thus, **originalSettings.volume** becomes **75** as well.

**Part B:**

To prevent modifying **originalSettings** you have to create a copy instead of modifying the reference. This can be done by making a shallow clone of the object using the spread operator

**Corrected Code:**

```js
// Fix this code so newSettings is a true copy
const originalSettings = { volume: 50, brightness: 80 };
const newSettings = { ...originalSettings };
newSettings.volume = 75;
console.log(originalSettings.volume);
```

---

## Prompt 3

Given this array of products and the code using `filter`:

```js
const products = [
  { name: "Laptop", price: 1000, inStock: true },
  { name: "Phone", price: 700, inStock: false },
  { name: "Watch", price: 300, inStock: true },
  { name: "Tablet", price: 500, inStock: true },
];

const itemsInStock = products.filter((product) => {
  return product.inStock;
});
```

Walk through what happens in the first iteration of filter:

- What is the value of `product`?
- What gets returned from the callback?
- What happens with that returned value?

### Response 3

Your response...
