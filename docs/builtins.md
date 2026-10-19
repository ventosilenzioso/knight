# Knight — Built-in Functions

| Function | Returns | Description |
|---|---|---|
| `abs(any)` | `float` | Absolute value. |
| `array(...)` | `array` | Construct an array. |
| `at(array, any)` | `any` | Indexed access. |
| `bool(any)` | `bool` | Truthiness conversion. |
| `ceil(any)` | `int` | Round up. |
| `clamp(any, any, any)` | `float` | Clamp a value into [lo, hi]. |
| `contains(any, any)` | `bool` | Substring test. |
| `del(map, any)` | `bool` | Remove a map key. |
| `distance(any, any, any, any, any, any)` | `float` | 3D Euclidean distance. |
| `ends_with(any, any)` | `bool` | Suffix test. |
| `float(any)` | `float` | Parse/convert to float. |
| `floor(any)` | `int` | Round down. |
| `format(any, ...)` | `string` | Substitute %s/%d/%f/%v. |
| `has(map, any)` | `bool` | Map key existence. |
| `int(any)` | `int` | Parse/convert to integer. |
| `is_array(any)` | `bool` | True for array. |
| `is_bool(any)` | `bool` | True for bool. |
| `is_map(any)` | `bool` | True for map. |
| `is_null(any)` | `bool` | True if the value is null. |
| `is_number(any)` | `bool` | True for int or float. |
| `is_string(any)` | `bool` | True for string. |
| `join(array, any)` | `string` | Join array elements into a string. |
| `keys(map)` | `array` | Array of map keys. |
| `len(any)` | `int` | Length of a string, array, or map. |
| `lower(any)` | `string` | Lowercase. |
| `map(...)` | `map` | Construct a map. |
| `max(any, any)` | `float` | Larger of two values. |
| `min(any, any)` | `float` | Smaller of two values. |
| `pop(array)` | `any` | Last element. |
| `pow(any, any)` | `float` | a raised to b. |
| `push(array, any)` | `array` | Append a value and return the array. |
| `random(any, any)` | `int` | Random integer. |
| `replace(any, any, any)` | `string` | Replace all occurrences. |
| `round(any)` | `int` | Nearest integer. |
| `shift(array)` | `any` | First element. |
| `split(any, any)` | `array` | Split a string into an array. |
| `sqrt(any)` | `float` | Square root. |
| `starts_with(any, any)` | `bool` | Prefix test. |
| `str(any)` | `string` | Convert any value to text. |
| `substr(any, any, any)` | `string` | Substring by rune offset. |
| `tostring(any)` | `string` | Alias of `str`. |
| `trim(any)` | `string` | Strip surrounding whitespace. |
| `typeof(any)` | `string` | Type name of a value. |
| `upper(any)` | `string` | Uppercase. |
| `values(map)` | `array` | Array of map values. |
