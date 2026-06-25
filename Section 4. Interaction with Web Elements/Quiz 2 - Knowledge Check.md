# Question 1

## HTML

```html
<div class="form-group row">
   <label class="col-sm-3 label">Radios</label>
</div>
```

## Question

How to find `<label>` web element by class value `"label"`?

### Options

1. `page.locator('[class="label"]')`    
2. `page.locator('class=label')`
3. `page.locator('.label')` ✅ Correct
4. `page.locator('class=".label"')`

---

## Correct Answer

```javascript
page.locator('.label')
```

---

## Why This Answer Is Correct

- `.label` is a standard CSS class selector.    
- The dot (`.`) represents a class selector in CSS.
- Playwright supports CSS selectors directly inside `locator()`.

This selector means:

> Find any element that contains the class `label`.

The actual HTML is:

```html
<label class="col-sm-3 label">Radios</label>
```

Since the element contains the class `label`, Playwright correctly finds it.

---

## Why Other Options Are Wrong

### ❌ Option 1

```javascript
page.locator('[class="label"]')
```

### Why Wrong

This searches for:

```html
class="label"
```

But the actual class attribute is:

```html
class="col-sm-3 label"
```

Because there are multiple classes, the selector does not match.

---

### ❌ Option 2

```javascript
page.locator('class=label')
```

### Why Wrong

- `class=label` is not valid Playwright locator syntax.    
- Playwright uses CSS selectors inside `locator()`.

Correct CSS class syntax:

```javascript
.label
```

---

### ❌ Option 4

```javascript
page.locator('class=".label"')
```

### Why Wrong

- This is invalid CSS syntax.    
- `class="..."` is HTML syntax, not Playwright locator syntax.

---

# Question 2

## HTML

```html
<div class="form-group row">
   <label class="col-sm-3 label">Radios</label>
</div>
```

## Question

What is the correct syntax to find `<label>` web element using a user-facing locator?

### Options

1. `page.getByRole('label')`    
2. `page.getByText('label')`
3. `page.getByTitle('Radios')`
4. `page.getByLabel('Radios')` ✅ Correct

---

## Correct Answer

```javascript
page.getByLabel('Radios')
```

---

## Why This Answer Is Correct

- `getByLabel()` is a user-facing locator.    
- It locates elements using visible label text.
- Users visually see the label `"Radios"`.

This follows Playwright best practices:

> Tests should mimic how real users interact with the application.

---

## Why Other Options Are Wrong

### ❌ Option 1

```javascript
page.getByRole('label')
```

### Why Wrong

- `label` is not a valid ARIA role.    
- `getByRole()` only works with valid accessibility roles such as:
    - button
    - textbox
    - checkbox
    - radio

---

### ❌ Option 2

```javascript
page.getByText('label')
```

### Why Wrong

- The visible text is `"Radios"`, not `"label"`.    

Correct usage would be:

```javascript
page.getByText('Radios')
```

---

### ❌ Option 3

```javascript
page.getByTitle('Radios')
```

### Why Wrong

- `getByTitle()` searches for the HTML `title` attribute.    
- The HTML does not contain:

```html
title="Radios"
```

So Playwright cannot find the element.

---

# Question 3

## HTML

```html
<div class="form-group row">
   <label class="col-sm-3 label">Radios</label>
</div>
```

## Question

How to find child element `<label>` from the parent `<div>`?

### Options

1. `page.getByRole('div').locator('label')`    
2. `page.locator('div-label')`
3. `page.locator('div label')` ✅ Correct
4. `page.locator('div').child('label')`

---

## Correct Answer

```javascript
page.locator('div label')
```

---

## Why This Answer Is Correct

In CSS selectors, a space means:

> Find descendant/child elements inside another element.

So:

```javascript
'div label'
```

means:

> Find a `<label>` inside a `<div>`.

This is the correct Playwright syntax for locating child elements.

---

## Why Other Options Are Wrong

### ❌ Option 1

```javascript
page.getByRole('div').locator('label')
```

### Why Wrong

- `div` is not a valid ARIA role.    
- `getByRole()` only accepts accessibility roles.

---

### ❌ Option 2

```javascript
page.locator('div-label')
```

### Why Wrong

- `div-label` is interpreted as a single HTML tag.    
- No HTML element named `div-label` exists.

---

### ❌ Option 4

```javascript
page.locator('div').child('label')
```

### Why Wrong

- Playwright does not have a `.child()` method.    
- Child locators are created using:
    - CSS descendant selectors
    - chained locators

---

# Question 4

## HTML

```html
<div class="form-group row">
   <label class="col-sm-3 label">Radios</label>
</div>
```

## Question

Save a `<div>` locator to a constant and then find a `<label>` locator reusing the constant.

### Options

```javascript
const parent = page.locator('div')
parent.getByRole('label')
```

```javascript
parent = page.locator('div')
parent.locator('label')
```

```javascript
const parent = page.locator('.label')
parent.locator('label')
```

```javascript
const parent = page.locator('.row')
parent.locator('label')
```

✅ Correct

---

## Correct Answer

```javascript
const parent = page.locator('.row')
parent.locator('label')
```

---

## Why This Answer Is Correct

- `.row` identifies the parent `<div>`.    
- `parent.locator('label')` searches for child labels inside the parent.
- This demonstrates proper locator reuse.

Benefits:

- Cleaner code
- Reduced duplication
- Easier maintenance

---

## Why Other Options Are Wrong

### ❌ Option 1

```javascript
const parent = page.locator('div')
parent.getByRole('label')
```

### Why Wrong

- `label` is not a valid ARIA role.    

---

### ❌ Option 2

```javascript
parent = page.locator('div')
parent.locator('label')
```

### Why Wrong

- Missing `const`.    
- Variable is not properly declared.

---

### ❌ Option 3

```javascript
const parent = page.locator('.label')
parent.locator('label')
```

### Why Wrong

- `.label` already selects the child `<label>`.    
- Then searching for another `label` inside it is incorrect.

---

# Question 5

## HTML

```html
<div class="form-group row">
   <label class="col-sm-3 label">Radios</label>
</div>
```

## Question

How to get text value `"Radios"` and assign it to a constant?

### Options

```javascript
const myConstant = await page.locator('.label').textContent()
```

✅ Correct

```javascript
const myConstant = await page.locator('.label').getText()
```

```javascript
const myConstant = await page.locator('.label').textValue()
```

```javascript
const myConstant = await page.locator('.label').inputValue()
```

---

## Correct Answer

```javascript
const myConstant = await page.locator('.label').textContent()
```

---

## Why This Answer Is Correct

- `textContent()` extracts visible text from HTML elements.    
- The label contains:

```html
Radios
```

So Playwright returns:

```javascript
"Radios"
```

---

## Why Other Options Are Wrong

### ❌ Option 2

```javascript
getText()
```

### Why Wrong

- Playwright does not have a `getText()` method.    

---

### ❌ Option 3

```javascript
textValue()
```

### Why Wrong

- `textValue()` is not a valid Playwright method.    

---

### ❌ Option 4

```javascript
inputValue()
```

### Why Wrong

- `inputValue()` only works with:    
    - input
    - textarea
    - select

A `<label>` is not an input element.

---

# Question 6

## HTML

```html
<div class="form-group row">
   <label class="col-sm-3 label">Radios</label>
</div>
```

## Question

Which assertion correctly validates the text `"Radios"` for the label?

### Options

```javascript
expect(page.locator('label')).toEqual('Radios')
```

```javascript
expect(await page.locator('label').textContent()).toEqual('Radios')
```

✅ Correct

```javascript
await expect(page.locator('label')).toEqual('Radios')
```

```javascript
expect(await page.locator('label')).toHaveText('Radios')
```

---

## Correct Answer

```javascript
expect(await page.locator('label').textContent()).toEqual('Radios')
```

---

## Why This Answer Is Correct

- `textContent()` extracts the actual text.    
- `toEqual()` compares the actual text with the expected text.

This is a valid general assertion.

---

## Why Other Options Are Wrong

### ❌ Option 1

```javascript
expect(page.locator('label')).toEqual('Radios')
```

### Why Wrong

- `page.locator('label')` returns a Locator object.    
- `"Radios"` is a string.
- A Locator object cannot be directly compared to a string.

---

### ❌ Option 3

```javascript
await expect(page.locator('label')).toEqual('Radios')
```

### Why Wrong

- `toEqual()` is a general assertion.    
- Locator assertions require methods like:

```javascript
toHaveText()
```

---

### ❌ Option 4

```javascript
expect(await page.locator('label')).toHaveText('Radios')
```

### Why Wrong

- `toHaveText()` is a locator assertion.    
- Locator assertions should not use `await` before the locator.

Correct syntax:

```javascript
await expect(page.locator('label')).toHaveText('Radios')
```

---

# Final Summary

| Topic               | Correct Syntax                        |
| ------------------- | ------------------------------------- |
| CSS Class Selector  | `page.locator('.label')`              |
| User-Facing Locator | `page.getByLabel('Radios')`           |
| Child Locator       | `page.locator('div label')`           |
| Reusing Locators    | `const parent = page.locator('.row')` |
| Extract Text        | `textContent()`                       |
| General Assertion   | `expect(value).toEqual()`             |
| Locator Assertion   | `await expect(locator).toHaveText()`  |
