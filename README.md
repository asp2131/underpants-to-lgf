# Complete Guide: Publishing Your Underpants Library to npm

This guide will help you transform your completed Underpants project into a publishable npm package that others can install and use.

## 1. Update Your package.json

Replace your current `package.json` with this updated version:

```json
{
  "name": "@your-github-username/underpants",
  "version": "1.0.0",
  "description": "Functional utility library - student implementation of underscore.js",
  "main": "underpants.js",
  "keywords": ["functional", "utilities", "underscore", "lodash", "functional-programming"],
  "author": "Your Name <your.email@example.com>",
  "license": "MIT",
  "repository": {
    "type": "git",
    "url": "https://github.com/your-github-username/underpants.git"
  },
  "bugs": {
    "url": "https://github.com/your-github-username/underpants/issues"
  },
  "homepage": "https://github.com/your-github-username/underpants#readme",
  "engines": {
    "node": ">=12.0.0"
  },
  "scripts": {
    "test": "mocha test/*.spec.js",
    "test:browser": "open index.html"
  },
  "devDependencies": {
    "chai": "^4.3.7",
    "mocha": "^10.2.0"
  },
  "files": [
    "underpants.js",
    "README.md",
    "LICENSE"
  ]
}
```

### Key Changes Made:
- **Removed `"private": true`** - This was preventing npm publishing
- **Changed name** to use your GitHub username as a scope (`@your-github-username/underpants`)
- **Updated license** from "CC" to "MIT" (more standard for npm packages)
- **Added `files` array** - Specifies exactly what gets published to npm
- **Updated repository URLs** - Point to your GitHub repo
- **Added keywords** - Help people find your package

**Important:** Replace `your-github-username`, `Your Name`, and `your.email@example.com` with your actual information!

## 2. Create Additional Required Files

### LICENSE File
Create a file named `LICENSE` (no extension) in your project root:

```
MIT License

Copyright (c) 2024 [Your Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

### Updated README.md
Replace your current README.md with this npm-focused version:

```markdown
# @your-github-username/underpants

A functional utility library implementing underscore.js-style functions. Created as part of a coding bootcamp exercise.

## Installation

```bash
npm install @your-github-username/underpants
```

## Usage

### Node.js
```javascript
const _ = require('@your-github-username/underpants');

console.log(_.identity(42)); // 42
console.log(_.first([1, 2, 3], 2)); // [1, 2]
console.log(_.map([1, 2, 3], x => x * 2)); // [2, 4, 6]
```

### Browser
```html
<script src="node_modules/@your-github-username/underpants/underpants.js"></script>
<script>
    console.log(_.identity(42)); // 42
</script>
```

## Available Functions

- `_.identity(value)` - Returns the value unchanged
- `_.typeOf(value)` - Returns the type of value as a string
- `_.first(array, n)` - Returns the first n elements of an array
- `_.last(array, n)` - Returns the last n elements of an array
- `_.indexOf(array, value)` - Returns the index of the first occurrence of value
- `_.contains(array, value)` - Returns true if array contains value
- `_.each(collection, function)` - Iterates over collection calling function for each element
- `_.unique(array)` - Returns array with duplicates removed
- `_.filter(array, predicate)` - Returns elements that pass the predicate test
- `_.reject(array, predicate)` - Returns elements that fail the predicate test
- `_.partition(array, predicate)` - Splits array into two arrays based on predicate
- `_.map(collection, function)` - Creates new array with results of calling function on each element
- `_.pluck(array, property)` - Extracts property values from array of objects
- `_.every(collection, predicate)` - Returns true if all elements pass predicate test
- `_.some(collection, predicate)` - Returns true if any element passes predicate test
- `_.reduce(array, function, seed)` - Reduces array to single value using function
- `_.extend(object, ...sources)` - Copies properties from sources to object

## Testing

Run the test suite:
```bash
npm test
```

Open browser tests:
```bash
npm run test:browser
```

## Development

This library was created as part of a coding bootcamp exercise to understand functional programming concepts and utility libraries like underscore.js and lodash.
```

**Remember:** Replace `@your-github-username` with your actual GitHub username throughout the README!

## 3. Publishing Steps

Follow these steps in order to publish your package to npm:

### Step 1: Ensure All Functions Are Implemented
Make sure you've completed all the function implementations in `underpants.js`. All tests should be passing:
```bash
npm test
```

### Step 2: Create npm Account
1. Go to [npmjs.com](https://npmjs.com)
2. Click "Sign Up" and create an account
3. Verify your email address

### Step 3: Test Your Package Locally
Before publishing, test that your package works:
```bash
# Test that your module can be required
node -e "console.log(require('./underpants.js').identity(42))"

# Test a few more functions
node -e "const _ = require('./underpants.js'); console.log(_.map([1,2,3], x => x*2))"
```

### Step 4: Login to npm
In your terminal, login to npm:
```bash
npm login
```
Enter your npm username, password, and email when prompted.

### Step 5: Publish Your Package
```bash
npm publish --access public
```

The `--access public` flag is required for scoped packages (packages with `@username/` in the name).

## 4. Using Your Published Package

Once published, anyone can install and use your library:

### Installation
```bash
npm install @your-github-username/underpants
```

### Usage Example
```javascript
const _ = require('@your-github-username/underpants');

// Test various functions
console.log(_.identity(42)); // 42
console.log(_.typeOf([1,2,3])); // "array"
console.log(_.first([1,2,3,4,5], 3)); // [1,2,3]
console.log(_.map([1,2,3], x => x * 2)); // [2,4,6]
console.log(_.filter([1,2,3,4,5], x => x % 2 === 0)); // [2,4]

// Use it with real data
const users = [
  {name: 'Alice', age: 25},
  {name: 'Bob', age: 30},
  {name: 'Carol', age: 28}
];

console.log(_.pluck(users, 'name')); // ['Alice', 'Bob', 'Carol']
console.log(_.every(users, user => user.age > 18)); // true
```

## 5. Updating Your Package

When you want to publish updates:

1. Make your changes
2. Update the version in `package.json`:
   ```json
   "version": "1.0.1"
   ```
3. Publish again:
   ```bash
   npm publish
   ```

## Troubleshooting

**Package name already exists:** Use a different scoped name like `@yourname/underpants-v2`

**Permission denied:** Make sure you're logged in with `npm whoami`

**Tests failing:** Fix your function implementations before publishing

**Module not found:** Check that your `main` field in package.json points to the correct file

Congratulations! You've now published your own npm package that others can install and use! 🎉
