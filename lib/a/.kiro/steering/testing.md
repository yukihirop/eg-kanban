<!-- Inclusion Mode: Conditional: "**/*.{test,spec}.{ts,tsx,js,jsx}" -->

# Testing Guidelines

## Test Framework
- Use Vitest for unit and integration tests
- React Testing Library for component tests

## File Organization
- Place test files next to the code they test: `Component.tsx` → `Component.test.tsx`
- Use `.test.ts` or `.test.tsx` extension

## Naming Conventions
```typescript
describe('ComponentName', () => {
  it('should do something specific', () => {
    // test implementation
  });
});
```

## Test Structure (AAA Pattern)
```typescript
it('should update task status', () => {
  // Arrange - setup test data
  const task = { id: 1, status: 'todo' };

  // Act - perform action
  const result = updateStatus(task, 'done');

  // Assert - verify result
  expect(result.status).toBe('done');
});
```

## Component Testing
```typescript
import { render, screen } from '@testing-library/react';
import { UserEvent } from '@testing-library/user-event';

it('should render task card', () => {
  render(<TaskCard title="Test Task" />);
  expect(screen.getByText('Test Task')).toBeInTheDocument();
});
```

## Best Practices
- One assertion per test when possible
- Use descriptive test names that explain the expected behavior
- Mock external dependencies (API calls, localStorage)
- Test user behavior, not implementation details
