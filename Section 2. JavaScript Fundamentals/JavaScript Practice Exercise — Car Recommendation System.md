In this exercise, we create a JavaScript function that recommends which car a family should rent based on:

- Family size
- Planned driving distance

---

# Requirements

Create two variables:

- `familySize`    
- `plannedDistanceToDrive`

Then create a function called `recommendedCar()` that returns a car recommendation based on the following conditions:

| Condition                                                    | Recommended Car |
| ------------------------------------------------------------ | --------------- |
| Family size is 4 or less AND distance is less than 200 miles | Tesla           |
| Family size is 4 or less AND distance is 200 miles or more   | Toyota Camry    |
| Family size is more than 4                                   | Minivan         |

---

# Starter Code

```javascript
let familySize = 2;

function recommendedCar(familySize) {

}

console.log(recommendedCar(familySize, plannedDistanceToDrive));
```

---

# Solution

## Step 1 — Create Variables

```javascript
let familySize = 2
let plannedDistanceToDrive = 100
```

---

## Step 2 — Create the Function

```javascript
function recommendedCar(familySize, plannedDistanceToDrive) {

	if (familySize <= 4 && plannedDistanceToDrive < 200) {
		return "Tesla"

	} else if (familySize <= 4 && plannedDistanceToDrive >= 200) {
		return "Toyota Camry"

	} else {
		return "Minivan"
	}

}
```

---

## Step 3 — Call the Function

```javascript
console.log(recommendedCar(familySize, plannedDistanceToDrive))
```

---

# Complete Code

```javascript
let familySize = 2
let plannedDistanceToDrive = 100

function recommendedCar(familySize, plannedDistanceToDrive) {

	if (familySize <= 4 && plannedDistanceToDrive < 200) {
		return "Tesla"

	} else if (familySize <= 4 && plannedDistanceToDrive >= 200) {
		return "Toyota Camry"

	} else {
		return "Minivan"
	}

}

console.log(recommendedCar(familySize, plannedDistanceToDrive))
```

---

# Example Outputs

## Example 1

```javascript
familySize = 2
plannedDistanceToDrive = 100
```

### Output

```javascript
Tesla
```

---

## Example 2

```javascript
familySize = 4
plannedDistanceToDrive = 300
```

### Output

```javascript
Toyota Camry
```

---

## Example 3

```javascript
familySize = 6
plannedDistanceToDrive = 150
```

### Output

```javascript
Minivan
```

---

# Concepts Used in This Exercise

| Concept                  | Purpose             |
| ------------------------ | ------------------- |
| Variables                | Store data          |
| Functions                | Reusable logic      |
| Parameters               | Accept input values |
| Conditional Statements   | Decision making     |
| Logical Operators (`&&`) | Combine conditions  |
| `return` keyword         | Return a value      |

---

# Logic Breakdown

## Condition 1

```javascript
familySize <= 4 && plannedDistanceToDrive < 200
```

- Small family    
- Short distance
- Recommend → Tesla

---

## Condition 2

```javascript
familySize <= 4 && plannedDistanceToDrive >= 200
```

- Small family    
- Long distance
- Recommend → Toyota Camry

---

## Condition 3

```javascript
familySize > 4
```

- Large family    
- Recommend → Minivan

---

# Important Notes

> [!note]  
> This exercise is a great example of combining:
> 
> - Functions
>     
> - Conditions
>     
> - Logical operators
>     
> - Return statements
>     

---

# Possible Improvements

You can improve this exercise later by:

- Adding more car types    
- Using arrays and objects
- Taking user input
- Converting it into a web application
- Writing automated tests using Playwright

---

# Summary

- We created variables to store input values.    
- We created a reusable function.
- We used conditional statements to make decisions.
- The function returned different car recommendations based on conditions.

---

# Final Notes

This is a foundational JavaScript exercise that demonstrates real-world decision-making logic and prepares you for more advanced programming concepts later in automation and web development.