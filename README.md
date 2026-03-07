# Probe

Probe is the assertion library and test framework for the Rockit programming language. It provides a comprehensive set of assertion functions for writing unit tests in Rockit.

## Import

```rockit
import rockit.test.probe
```

## Available Assertions

### Core

| Function | Description |
|----------|-------------|
| `assert(condition: Bool, message: String = "")` | Passes if condition is true |
| `assertTrue(condition: Bool, message: String = "")` | Passes if condition is true |
| `assertFalse(condition: Bool, message: String = "")` | Passes if condition is false |
| `fail(message: String = "test failed")` | Unconditionally fails the test |

### Equality

| Function | Description |
|----------|-------------|
| `assertEquals(expected: Int, actual: Int, message: String = "")` | Passes if two integers are equal |
| `assertEqualsStr(expected: String, actual: String, message: String = "")` | Passes if two strings are equal |
| `assertEqualsBool(expected: Bool, actual: Bool, message: String = "")` | Passes if two booleans are equal |
| `assertNotEquals(a: Int, b: Int, message: String = "")` | Passes if two integers are not equal |
| `assertNotEqualsStr(a: String, b: String, message: String = "")` | Passes if two strings are not equal |

### Comparison

| Function | Description |
|----------|-------------|
| `assertGreaterThan(a: Int, b: Int, message: String = "")` | Passes if a > b |
| `assertLessThan(a: Int, b: Int, message: String = "")` | Passes if a < b |
| `assertGreaterThanOrEqual(a: Int, b: Int, message: String = "")` | Passes if a >= b |
| `assertLessThanOrEqual(a: Int, b: Int, message: String = "")` | Passes if a <= b |
| `assertBetween(value: Int, low: Int, high: Int, message: String = "")` | Passes if low <= value <= high |

### String

| Function | Description |
|----------|-------------|
| `assertStringContains(haystack: String, needle: String, message: String = "")` | Passes if haystack contains needle |
| `assertStartsWith(s: String, prefix: String, message: String = "")` | Passes if s starts with prefix |
| `assertEndsWith(s: String, suffix: String, message: String = "")` | Passes if s ends with suffix |
| `assertStringEmpty(s: String, message: String = "")` | Passes if s is the empty string |
| `assertStringNotEmpty(s: String, message: String = "")` | Passes if s is not the empty string |
| `assertStringLength(s: String, expected: Int, message: String = "")` | Passes if the length of s equals expected |

## Usage

Every assertion function accepts an optional `message` parameter. When an assertion fails, Probe calls `panic()` with a diagnostic message that includes the expected and actual values along with the custom message, if provided.

### Basic test file

```rockit
import rockit.test.probe

fun main(): Unit {
    assertEquals(2, 1 + 1, "basic addition")
    assertTrue(10 > 5)
    assertEqualsStr("hello", "hello", "string match")
    assertStringContains("rockit-probe", "probe", "substring check")
    println("All tests passed.")
}
```

### Recording mode

Probe supports a recording mode activated by setting `__probeRecording = 1`. In this mode, assertions do not panic on failure. Instead, they append pass/fail results to the `__probeResults` string and increment `__probeFailed` for each failure. This is used internally by the `rockit test --detailed` command to collect results across all assertions before reporting.

## License

Proprietary -- Dark Matter Tech. All rights reserved.
