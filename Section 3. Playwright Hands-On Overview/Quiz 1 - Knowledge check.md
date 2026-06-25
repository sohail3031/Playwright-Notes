# Question 1

## Which command is used to set up the Playwright framework from scratch as an independent project?

- `npx init playwright`    
- `npm init playwright@latest`
- `npm install playwright@latest`
- `npx install playwright`

### Correct Answer

```bash
npm init playwright@latest
```

### Explanation

This command initializes a brand-new Playwright project using the latest Playwright setup template.

It:

- Creates project structure
- Installs Playwright
- Generates config files
- Adds example tests
- Installs browsers

### Why the Other Options Are Wrong

#### `npx init playwright`

- Incorrect command
- `init` is not used this way with Playwright

#### `npm install playwright@latest`

- Only installs the package
- Does not create project structure or config files

#### `npx install playwright`

- Invalid command
- Playwright does not provide installation using this syntax

---

# Question 2

## Which command is correct to run a test with the title `"first test"` in headed mode for the `"chromium"` project?

- `npm playwright test --project=first test --headed -g chromium`
- `npm playwright test --project=chromium "first test" -g --headed`
- `npx playwright test --project=chromium -headed -g first test`
- `npx playwright test --project=chromium -g "first test" --headed`

### Correct Answer

```bash
npx playwright test --project=chromium -g "first test" --headed
```

### Explanation

This command:

- Uses `npx playwright test` to run tests
- Runs only the `chromium` project
- Uses `-g` to match the test title
- Runs in headed mode using `--headed`

### Why the Other Options Are Wrong

#### `npm playwright test --project=first test --headed -g chromium`

- Incorrect syntax
- `npm playwright` is invalid
- `--project` should contain browser project name, not test title

#### `npm playwright test --project=chromium "first test" -g --headed`

- Invalid command format
- `npm playwright` does not exist
- `-g` requires a value immediately after it

#### `npx playwright test --project=chromium -headed -g first test`

- Incorrect flag
- Should use `--headed`, not `-headed`
- Test title should be wrapped in quotes

---

# Question 3

## What is a test trace?

- Screenshot of the test result    
- Text log of the test execution
- The sequence of page snapshots with logs

### Correct Answer

```text
The sequence of page snapshots with logs
```

### Explanation

A Playwright trace records:

- Page snapshots
- Actions performed
- Network activity
- Console logs    
- Screenshots
- Timing information

It helps debug failed tests visually.

### Why the Other Options Are Wrong

#### `Screenshot of the test result`

- A trace contains much more than screenshots

#### `Text log of the test execution`

- Traces are visual and interactive, not only text logs

---

# Question 4

## What is the correct command to mark a test to be ignored during test execution?

- `test.ignore()`    
- `test.skip()`
- `test.false()`
- `test.exclude()`

### Correct Answer

```typescript
test.skip()
```

### Explanation

`test.skip()` tells Playwright not to execute the test.

Example:

```typescript
test.skip("test name", async ({ page }) => {

});
```

### Why the Other Options Are Wrong

#### `test.ignore()`

- Does not exist in Playwright

#### `test.false()`

- Invalid Playwright API

#### `test.exclude()`

- Not a valid Playwright method

---

# Question 5

## What command is used to group tests into suites within a single spec file?

- `describe()`    
- `test.describe()`
- `context()`
- `test.context()`

### Correct Answer

```typescript
test.describe()
```

### Explanation

`test.describe()` is used to organize related tests into logical groups.

Example:

```typescript
test.describe("Login Tests", () => {

});
```

### Why the Other Options Are Wrong

#### `describe()`

- Used in frameworks like Jest or Mocha
- Not the recommended Playwright syntax

#### `context()`

- Not used for grouping tests in Playwright

#### `test.context()`

- Invalid Playwright API

---

# Question 6

## What is the correct hook name to repeat code at the beginning of each test?

- `before()`    
- `test.before()`
- `beforeEach()`
- `test.beforeEach()`

### Correct Answer

```typescript
test.beforeEach()
```

### Explanation

`test.beforeEach()` runs before every test.

Used for:

- Navigation
- Login setup
- Test preparation
- Common initialization steps

Example:

```typescript
test.beforeEach(async ({ page }) => {
    await page.goto("http://localhost:4200/");
});
```

### Why the Other Options Are Wrong

#### `before()`

- Not valid Playwright syntax

#### `test.before()`

- Does not exist in Playwright

#### `beforeEach()`

- Exists in some testing frameworks
- Playwright uses `test.beforeEach()`

