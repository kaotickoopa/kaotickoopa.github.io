---
layout: post
title: "Mastering Unit Testing in React with Jest and React Testing Library"
date: 2024-10-28
author: "Mason"
tags: ["React", "Testing", "Jest", "Best Practices"]
---

Unit testing is crucial for building reliable React applications. In this post, I'll share best practices and patterns I've learned while testing complex React components.

## Why Testing Matters

Good tests:
- Catch bugs before production
- Document expected behavior
- Reduce regression issues
- Enable confident refactoring
- Improve code quality

## Testing Tools

### Jest
- **Framework**: Provides test runner, assertion library, and mocking utilities
- **Snapshots**: Useful for UI regression testing
- **Coverage**: Built-in coverage reporting

### React Testing Library
- **Philosophy**: "Test behavior, not implementation details"
- **Queries**: User-centric queries (getByRole, getByLabelText, etc.)
- **Async**: Built-in support for async operations with waitFor

## Testing Patterns

### 1. Component Rendering
```javascript
import { render, screen } from '@testing-library/react';

test('renders component', () => {
  render(<MyComponent />);
  expect(screen.getByText('Hello')).toBeInTheDocument();
});
```

### 2. User Interactions
```javascript
import userEvent from '@testing-library/user-event';

test('handles click events', async () => {
  const user = userEvent.setup();
  render(<Button onClick={handleClick}>Click me</Button>);
  
  await user.click(screen.getByRole('button'));
  expect(handleClick).toHaveBeenCalled();
});
```

### 3. Form Input
```javascript
test('updates input value', async () => {
  const user = userEvent.setup();
  render(<Input />);
  
  await user.type(screen.getByRole('textbox'), 'hello');
  expect(screen.getByRole('textbox')).toHaveValue('hello');
});
```

### 4. Async Operations
```javascript
test('fetches and displays data', async () => {
  render(<DataFetcher />);
  
  // Wait for loading to disappear
  await waitFor(() => {
    expect(screen.queryByText('Loading')).not.toBeInTheDocument();
  });
  
  // Verify data is displayed
  expect(screen.getByText('Data')).toBeInTheDocument();
});
```

### 5. Mocking
```javascript
jest.mock('axios');

test('handles API calls', async () => {
  axios.get.mockResolvedValue({ data: { id: 1, name: 'Test' } });
  
  render(<Component />);
  
  await waitFor(() => {
    expect(screen.getByText('Test')).toBeInTheDocument();
  });
});
```

## Common Testing Patterns

### Setup and Teardown
```javascript
beforeEach(() => {
  // Reset mocks before each test
  jest.clearAllMocks();
});

afterEach(() => {
  // Cleanup after each test
  jest.restoreAllMocks();
});
```

### Custom Render Function
```javascript
function renderWithProviders(component) {
  return render(
    <Provider store={store}>
      {component}
    </Provider>
  );
}

test('uses custom render', () => {
  renderWithProviders(<App />);
  // Tests run with Provider context
});
```

## Testing Best Practices

1. **Test Behavior, Not Implementation**
   - ❌ Test if state changed
   - ✅ Test if UI updated correctly

2. **Use Semantic Queries**
   - ✅ `getByRole('button', { name: /save/i })`
   - ❌ `getByTestId('saveButton')`

3. **Avoid Implementation Details**
   - ✅ Mock APIs at boundaries
   - ❌ Mock internal functions

4. **Write Meaningful Assertions**
   ```javascript
   // ✅ Good
   expect(screen.getByRole('button')).toBeEnabled();
   
   // ❌ Not as clear
   expect(button.disabled).toBe(false);
   ```

5. **Test User Workflows**
   ```javascript
   // Test complete user journey
   test('complete checkout flow', async () => {
     render(<CheckoutPage />);
     // Fill form
     // Submit
     // Verify success
   });
   ```

## Coverage Goals

- **Statements**: 80%+
- **Branches**: 75%+
- **Functions**: 80%+
- **Lines**: 80%+

## Debugging Tests

### Useful Methods
```javascript
// Print DOM
screen.debug();

// Get all text
screen.logTestingPlaygroundURL();

// Wait with timeout
await waitFor(() => {
  expect(element).toBeInTheDocument();
}, { timeout: 3000 });
```

## Common Pitfalls

1. **Testing Implementation Details**: Focus on user behavior
2. **Fragile Selectors**: Use semantic queries instead of test IDs
3. **Not Waiting for Async**: Always use waitFor for async operations
4. **Too Many Mocks**: Mock at boundaries, not internals
5. **Skipping Edge Cases**: Test error states and edge cases

## Conclusion

Effective testing is about understanding what users see and interact with. By following these patterns and best practices, you can write tests that catch real bugs and serve as living documentation.

Start small, test critical paths first, and gradually increase coverage. Happy testing!

---

What testing patterns have helped you the most? Share in the comments!
