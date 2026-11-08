---
name: writing-unit-tests
description: Skill to write comprehensive, maintainable unit tests. Use this skill whenever a task involves writing or modifying Java unit tests without Spring Context.
---

## 1. Objective

Write comprehensive, maintainable unit tests for Java classes using **JUnit 5** and **Mockito**.

The primary objective is to achieve the maximum practical code coverage while ensuring that tests verify actual behavior, business rules, edge cases, and interactions with external dependencies.

Tests must be deterministic, independent, readable, and focused on one behavior at a time.

## 2. Scope

Write unit tests for **all public methods** of the target class, with the following exclusions:

- Getters and setters.
- DTO classes (Data Transfer Objects).
- Exception classes that contain no specific business logic.
- Constructors that only assign dependencies or initialize fields without specific logic.

Do not exclude methods simply because they are short or appear trivial. If a public method contains business logic, it must be tested.

For each public method, identify and cover:
- Normal execution scenarios.
- Boundary conditions.
- Invalid inputs.
- Null and empty inputs, where applicable.
- All possible branches and conditional paths.
- Exceptions and error-handling scenarios.
- Interactions with external dependencies.

## 3. JUnit 5 Requirements

Use JUnit 5 (`org.junit.jupiter.api`) for all tests.

### 3.1. Parameterized tests

Prefer parameterized tests whenever multiple input values exercise the same behavior.

Use the following annotations:

**@EnumSource**
- Use `@EnumSource` to cover all possible values of an enum.
- Every enum constant must be tested unless there is a documented reason to exclude it.
- Do not manually enumerate enum values using separate test methods.

**@ValueSource**
- Use `@ValueSource` to test multiple primitive values and strings.
- Cover meaningful boundary values, valid inputs, and invalid inputs.
- Include zero, negative numbers, minimum/maximum relevant values, and empty strings where applicable.

**@NullSource**
- Use `@NullSource` to test null arguments whenever the method accepts nullable inputs or has explicit null-handling behavior.

**@EmptySource**
- Use `@EmptySource` to test empty strings, collections, arrays, or other supported empty types when applicable.

Combine parameter sources when useful:

- `@NullSource`
- `@EmptySource`
- `@ValueSource`
- `@EnumSource`

Use `@MethodSource` for complex objects, multiple arguments, and scenarios that cannot be expressed conveniently with the annotations above.

### 3.2. Test naming

Use descriptive test names that explain the scenario and expected behavior.

Prefer:

`methodName_condition_expectedResult`

Examples:
- `calculateDiscount_whenCustomerIsPremium_returnsDiscountedPrice`
- `findUser_whenUserDoesNotExist_throwsUserNotFoundException`
- `process_whenInputIsNull_throwsIllegalArgumentException`

Use `@DisplayName` when it improves readability.

### 3.3. Test structure

Follow the Arrange-Act-Assert (AAA) pattern:

1. **Arrange:** Prepare input data, dependencies, and expected results.
2. **Act:** Execute the method being tested.
3. **Assert:** Verify the result, exception, or interactions.

Each test should verify one logical behavior.

Avoid unnecessary assertions and duplicated setup.

## 4. Mockito Requirements

Use Mockito whenever the class under test has external dependencies, including repositories, services, clients, gateways, or other collaborators.

### 4.1. Creating mocks

Always create mock objects using:

`org.mockito.Mockito.mock(Class.class)`

Do not use:
- `@Mock`
- `@InjectMocks`
- `@Mockito` or other mock-injection annotations.

Instantiate the class under test explicitly and pass its dependencies through the constructor or appropriate initialization mechanism.

Example:

```java
UserRepository repository = Mockito.mock(UserRepository.class);
UserService service = new UserService(repository);
```

This makes dependencies explicit and avoids hidden test initialization.

### 4.2. Stubbing

Use Mockito's `when().thenReturn()` and `when().thenThrow()` to define dependency behavior.

Examples:

```java
Mockito.when(repository.findById(1L))
       .thenReturn(Optional.of(user));

Mockito.when(repository.findById(2L))
       .thenThrow(new RuntimeException("Database error"));
```

Use `doReturn()`, `doThrow()`, or other appropriate Mockito alternatives when necessary, such as for void methods or spies.

Do not stub methods that are not needed by the scenario.

### 4.3. Verifying interactions

Mock interactions must be verified explicitly whenever they are relevant to the behavior being tested.

Use:

- `Mockito.verify()` to verify that a dependency method was called with the expected arguments and number of invocations.
- `Mockito.verifyNoMoreInteractions()` to ensure no unexpected additional interactions occurred.
- `Mockito.verifyNoInteractions()` to ensure a dependency was not used at all.

Examples:

```java
Mockito.verify(repository).save(user);

Mockito.verifyNoMoreInteractions(repository);

Mockito.verifyNoInteractions(notificationService);
```

Use interaction verification to ensure that:
- Expected dependencies are called.
- Methods receive correct arguments.
- Calls happen the expected number of times.
- Dependencies are not called when they should not be.
- No unexpected interactions occur.

Do not add `verifyNoMoreInteractions()` mechanically to every test. Use it when the absence of additional calls is part of the intended behavior and the test benefits from strict interaction verification.

## 5. Coverage Strategy

Aim for the maximum possible line, branch, and condition coverage.

For every public method:

1. Identify all conditional statements (`if`, `else`, `switch`, ternary operators).
2. Identify all possible branches and outcomes.
3. Identify loops and their zero, one, and multiple-iteration scenarios.
4. Identify exception paths.
5. Identify null, empty, and boundary input conditions.
6. Identify all enum values and ensure they are covered.
7. Identify dependency interactions and verify expected behavior.
8. Identify early returns and test each relevant path.

Pay special attention to:
- `null` arguments.
- Empty collections and strings.
- Collections containing null elements, when supported.
- Zero and negative numeric values.
- Maximum and minimum allowed values.
- Duplicate elements.
- Missing entities.
- Unexpected dependency responses.
- Exceptions thrown by dependencies.
- All enum constants.
- Boolean combinations in complex conditions.

Do not write tests merely to execute lines. Tests must assert meaningful outcomes.

Do not modify production code solely to increase test coverage unless explicitly requested.

## 6. Test Quality Rules

- Tests must be independent and must not depend on execution order.
- Do not share mutable test data between test cases.
- Do not use real databases, external APIs, network connections, or filesystem dependencies unless explicitly required for an integration test.
- Avoid unnecessary mocking of simple value objects.
- Do not mock the class under test.
- Avoid testing private methods directly. Test their behavior through public methods.
- Do not duplicate production implementation logic inside tests.
- Use clear and meaningful test data.
- Assert returned values, state changes, exceptions, and relevant interactions.
- Do not introduce arbitrary sleeps or timing-dependent assertions.
- Do not catch exceptions manually when `assertThrows()` can be used.
- Keep test methods focused and reasonably small.

## 7. Recommended JUnit 5 Assertions

Prefer:
- `Assertions.assertEquals()`
- `Assertions.assertNotEquals()`
- `Assertions.assertTrue()`
- `Assertions.assertFalse()`
- `Assertions.assertNull()`
- `Assertions.assertNotNull()`
- `Assertions.assertThrows()`
- `Assertions.assertAll()`

Use `assertThrows()` to verify expected exceptions and, when relevant, assert their messages.

## 8. Example

### Production class

```java
public class UserService {

    private final UserRepository repository;

    public UserService(UserRepository repository) {
        this.repository = repository;
    }

    public User findUser(Long id) {
        if (id == null || id <= 0) {
            throw new IllegalArgumentException("Invalid user ID");
        }

        return repository.findById(id)
                .orElseThrow(
                    () -> new UserNotFoundException("User not found")
                );
    }

    public boolean isEligible(UserStatus status) {
        return switch (status) {
            case ACTIVE -> true;
            case INACTIVE, BLOCKED -> false;
        };
    }
}
```

### Unit tests

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.EnumSource;
import org.junit.jupiter.params.provider.NullSource;
import org.junit.jupiter.params.provider.ValueSource;

import org.mockito.Mockito;

import java.util.Optional;

import static org.junit.jupiter.api.Assertions.*;

class UserServiceTest {

    private UserRepository repository;
    private UserService service;

    @BeforeEach
    void setUp() {
        repository = Mockito.mock(UserRepository.class);
        service = new UserService(repository);
    }

    @Test
    void findUser_whenUserExists_returnsUser() {
        User user = new User(1L, "John");

        Mockito.when(repository.findById(1L))
                .thenReturn(Optional.of(user));

        User result = service.findUser(1L);

        assertEquals(user, result);

        Mockito.verify(repository).findById(1L);
        Mockito.verifyNoMoreInteractions(repository);
    }

    @Test
    void findUser_whenUserDoesNotExist_throwsException() {
        Mockito.when(repository.findById(1L))
                .thenReturn(Optional.empty());

        assertThrows(
                UserNotFoundException.class,
                () -> service.findUser(1L)
        );

        Mockito.verify(repository).findById(1L);
        Mockito.verifyNoMoreInteractions(repository);
    }

    @ParameterizedTest
    @NullSource
    @ValueSource(longs = {0L, -1L, -100L})
    void findUser_whenIdIsInvalid_throwsException(Long id) {
        assertThrows(
                IllegalArgumentException.class,
                () -> service.findUser(id)
        );

        Mockito.verifyNoInteractions(repository);
    }

    @ParameterizedTest
    @EnumSource(UserStatus.class)
    void isEligible_whenStatusIsProvided_returnsExpectedResult(
            UserStatus status) {

        boolean result = service.isEligible(status);

        assertEquals(
                status == UserStatus.ACTIVE,
                result
        );

        Mockito.verifyNoInteractions(repository);
    }
}
```

## 9. Final Checklist

Before considering the task complete, verify the following:

- [ ] Every public method containing business logic has tests.
- [ ] Getters, setters, DTOs, simple exception classes, and constructors without specific logic are excluded.
- [ ] Every enum constant is covered using `@EnumSource`.
- [ ] Relevant values and boundaries are covered using `@ValueSource`.
- [ ] Null inputs are covered using `@NullSource` where applicable.
- [ ] Empty inputs are covered using `@EmptySource` where applicable.
- [ ] Complex scenarios use `@MethodSource` when appropriate.
- [ ] All relevant dependency interactions are verified.
- [ ] `verifyNoInteractions()` is used for scenarios where dependencies must not be called.
- [ ] `verifyNoMoreInteractions()` is used where strict interaction verification is appropriate.
- [ ] Exception scenarios are covered.
- [ ] All relevant branches and conditional paths are tested.
- [ ] Tests follow the Arrange-Act-Assert pattern.
- [ ] No unnecessary mock annotations are used.
- [ ] The test suite compiles and passes.
- [ ] Coverage results have been reviewed, and any uncovered relevant branches have been addressed.

**Final objective:** Produce a comprehensive unit test suite that verifies the behavior of every relevant public method, covers all meaningful execution paths, and achieves the highest practical code coverage without compromising test quality or maintainability.