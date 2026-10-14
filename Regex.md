# Regex Cheat Sheet – JavaScript / TypeScript

## 1. Regex Flags

| Flag | Meaning | Example |
|---|---|---|
| g | Global – find all matches | `/abc/g` |
| i | Case-insensitive | `/abc/i` |
| m | Multiline – `^` and `$` work per line | `/abc/m` |
| s | DotAll – `.` also matches line breaks | `/a.b/s` |

Flags can be combined, for example: `/[aeiou]/gi`

## 2. Character Classes

| Pattern | Meaning | Example |
|---|---|---|
| `[abc]` | Matches a, b, or c | `/[abc]/` |
| `[aeiou]` | Matches any vowel | `/[aeiou]/gi` |
| `[a-z]` | Matches lowercase letters | `/[a-z]/g` |
| `[A-Z]` | Matches uppercase letters | `/[A-Z]/g` |
| `[0-9]` | Matches digits from 0 to 9 | `/[0-9]/g` |
| `[a-zA-Z]` | Matches English letters | `/[a-zA-Z]/g` |
| `[^abc]` | Matches any character except a, b, or c | `/[^abc]/g` |
| `[^0-9]` | Matches non-digit characters | `/[^0-9]/g` |

## 3. Special Characters

| Pattern | Meaning |
|---|---|
| `.` | Any character except line terminators, by default |
| `^` | Beginning of input; beginning of each line with `m` |
| `$` | End of input; end of each line with `m` |
| `\` | Escapes a special character |
| `\d` | Any digit |
| `\D` | Any non-digit |
| `\w` | Word character: letters, digits, underscore |
| `\W` | Non-word character |
| `\s` | Whitespace: spaces, tabs, line breaks |
| `\S` | Non-whitespace character |
| `\b` | Word boundary |
| `\B` | Not a word boundary |

Examples:
- `/\d/g` — Find digits.
- `/\s/g` — Find whitespace.
- `/\bHello\b/i` — Find the whole word "Hello", case-insensitively.
- `/\./g` — Find a literal dot.

## 4. Quantifiers

| Pattern | Meaning | Example |
|---|---|---|
| `*` | Zero or more occurrences | `/ab*/` |
| `+` | One or more occurrences | `/ab+/` |
| `?` | Zero or one occurrence | `/colou?r/` |
| `{3}` | Exactly 3 occurrences | `/\d{3}/` |
| `{2,4}` | Between 2 and 4 occurrences | `/\d{2,4}/` |
| `{2,}` | At least 2 occurrences | `/\d{2,}/` |

## 5. Greedy and Lazy Matching

| Pattern | Meaning |
|---|---|
| `.*` | Greedy – matches as much as possible |
| `.*?` | Lazy – matches as little as possible |
| `.+` | One or more characters, greedy |
| `.+?` | One or more characters, lazy |

## 6. Groups and Alternatives

| Pattern | Meaning | Example |
|---|---|---|
| `(abc)` | Capturing group | `/(abc)/` |
| `(?:abc)` | Non-capturing group | `/(?:abc)/` |
| `a|b` | Matches a or b | `/cat|dog/` |
| `(ab)+` | One or more repetitions of "ab" | `/(ab)+/` |
| `(a)(b)` | Two separate capturing groups | `/(a)(b)/` |

## 7. Common Practical Patterns

| Requirement | Pattern |
|---|---|
| Find vowels | `/[aeiou]/gi` |
| Remove vowels | `/[aeiou]/gi` |
| Find digits | `/\d/g` |
| Match only digits | `/^\d+$/` |
| Find lowercase letters | `/[a-z]/g` |
| Find uppercase letters | `/[A-Z]/g` |
| Find alphanumeric characters | `/[a-z0-9]/gi` |
| Find whitespace | `/\s/g` |
| Find consecutive whitespace | `/\s+/g` |
| Find repeated characters | `/(.)\1+/g` |
| Find words beginning with A | `/\bA\w*/gi` |
| Find a word exactly | `/\bhello\b/i` |
| Find text between parentheses | `/\((.*?)\)/g` |
| Find a literal dot | `/\./g` |
| Find non-digit characters | `/\D/g` |

Note: These are practice patterns. For strict email, phone number, or other format validation, the appropriate pattern depends on the exact requirements.

## 8. JavaScript / TypeScript Regex Methods

### test() – Returns true or false
```typescript
console.log(/\d+/.test("123"));  // true
console.log(/\d+/.test("abc"));  // false
```

### match() – Returns matching text
```typescript
console.log("abc123".match(/\d+/)); // ["123"]
```

### replace() – Replaces matching text
```typescript
console.log("Hello World".replace(/[aeiou]/gi, ""));
// Hll Wrld
```

### split() – Splits a string using a pattern
```typescript
console.log("apple,banana orange".split(/[ ,]+/));
// ["apple", "banana", "orange"]
```

## 9. Important Difference: test() vs match() vs replace()

- `test()` checks whether a match exists and returns a boolean.
- `match()` retrieves matching text.
- `replace()` replaces matching text and returns a new string.
- `split()` divides a string wherever the pattern matches.

## 10. Important Reminders

1. Regex is written between `/ /` when using a regex literal.
2. Flags are written after the closing `/`.
3. `g` finds all matches; without it, many string methods work with only the first match.
4. `i` ignores case.
5. `^` and `$` are useful for validating an entire string.
6. `+` means one or more; `*` means zero or more.
7. `[]` defines a character set; `()` groups expressions.
8. Regex patterns may need adjustment depending on the input and validation requirements.
