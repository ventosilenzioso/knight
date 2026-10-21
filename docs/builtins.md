# Knight — Built-in Functions

Language built-ins need no include and are resolved before natives. All 60 are
listed below.

## Conversions and types

| Function | Returns | Description |
|---|---|---|
| `len(any)` | `int` | Length of a string, array or map. |
| `str(any)` | `string` | Convert any value to text. |
| `tostring(any)` | `string` | Alias of `str`. |
| `int(any)` | `int` | Parse/convert to integer. |
| `float(any)` | `float` | Parse/convert to float. |
| `bool(any)` | `bool` | Truthiness conversion. |
| `typeof(any)` | `string` | Type name of a value. |
| `is_null(any)` | `bool` | True if the value is null. |
| `is_number(any)` | `bool` | True for int or float. |
| `is_string(any)` | `bool` | True for string. |
| `is_bool(any)` | `bool` | True for bool. |
| `is_array(any)` | `bool` | True for array. |
| `is_map(any)` | `bool` | True for map. |

## Numbers

| Function | Returns | Description |
|---|---|---|
| `abs(number)` | `float` | Absolute value. |
| `round(number)` | `int` | Nearest integer. |
| `floor(number)` | `int` | Round down. |
| `ceil(number)` | `int` | Round up. |
| `sqrt(number)` | `float` | Square root. |
| `pow(base, exponent)` | `float` | Raise to a power. |
| `min(a, b)` | `float` | Smaller of two values. |
| `max(a, b)` | `float` | Larger of two values. |
| `clamp(value, lo, hi)` | `float` | Clamp into `[lo, hi]`. |
| `random()` / `random(n)` / `random(a, b)` | `int` | Random int: any, `0..n-1`, or inclusive range. |
| `sign(number)` | `int` | `-1`, `0` or `1`. |

## Strings

| Function | Returns | Description |
|---|---|---|
| `upper(text)` | `string` | Uppercase. |
| `lower(text)` | `string` | Lowercase. |
| `trim(text)` | `string` | Strip surrounding whitespace. |
| `substr(text, start, length)` | `string` | Substring by rune offset. |
| `contains(text, part)` | `bool` | Substring test. |
| `starts_with(text, prefix)` | `bool` | Prefix test. |
| `ends_with(text, suffix)` | `bool` | Suffix test. |
| `replace(text, old, new)` | `string` | Replace all occurrences. |
| `split(text, separator)` | `array` | Split into an array. |
| `join(array, separator)` | `string` | Join elements into one string. |
| `repeat(text, count)` | `string` | Repeat text. |
| `char(code)` | `string` | Character for a code point. |
| `char_code(text)` | `int` | Code point of the first character. |
| `count(text, part)` | `int` | Non-overlapping occurrences. |
| `pad_left(text, width, fill)` | `string` | Pad on the left. |
| `pad_right(text, width, fill)` | `string` | Pad on the right. |
| `starts_with_any(text, prefixes)` | `bool` | Matches any prefix in the array. |

## Arrays and maps

| Function | Returns | Description |
|---|---|---|
| `array(...)` | `array` | Construct an array. |
| `map(key, value, ...)` | `map` | Construct a map. |
| `push(array, value)` | `array` | Append **in place** and return the array. |
| `pop(array)` | `any` | Remove and return the last element. |
| `shift(array)` | `any` | Remove and return the first element. |
| `at(array\|map, index\|key)` | `any` | Element by index or key; `null` when absent. |
| `keys(map)` | `array` | Sorted key list. |
| `values(map)` | `array` | Value list. |
| `has(map, key)` | `bool` | Key existence. |
| `del(map, key)` | `bool` | Delete a key **in place**. |
| `insert(array, value, index)` | `array` | New array with value inserted. |
| `slice(array\|string, start, end)` | `any` | Copy of the `[start, end)` range. |
| `index_of(array\|map, value)` | `int` | Index/key position or `-1`. |
| `reverse(array)` | `array` | New reversed array. |
| `sort(array)` | `array` | New sorted array (numbers numerically). |
| `concat(a, b)` | `array` | New array with both appended. |
| `unique(array)` | `array` | New array without duplicates. |

`push`, `pop`, `shift` and `del` mutate the container in place, so both forms
work:

```knight
let list = [];
push(list, 10);          // list is now [10]
let last = pop(list);    // 10, list is []
list = push(list, 1);    // the reassigning form still works
```

`insert` always returns a new array and never modifies its input.

## Helpers

| Function | Returns | Description |
|---|---|---|
| `format(pattern, ...)` | `string` | Substitute `%s` / `%d` / `%f` / `%v`. |
| `distance(x1, y1, z1, x2, y2, z2)` | `float` | 3D Euclidean distance. |

## Slices and indexing

`slice(a, i, j)` is equivalent to `a[i:j]`; strings can also be indexed
directly (`"Knight"[2]` is `"i"`) and negative or out-of-range bounds are
clamped rather than raising an error.
