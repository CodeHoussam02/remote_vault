
# Python Cheatsheet: OS and Pathlib Modules

## OS Module

### Basics
```python
import os

# Get current working directory
cwd = os.getcwd()
print("Current Working Directory:", cwd)

# Change directory
os.chdir('/path/to/directory')
print("Changed Directory:", os.getcwd())

# List files and directories
files = os.listdir('.')
print("Files and Directories:", files)

# Create a directory
os.mkdir('new_directory')

# Remove a directory
os.rmdir('new_directory')

# Check if a path exists
exists = os.path.exists('some_path')
print("Path Exists:", exists)
```

### File Operations
```python
# Rename a file or directory
os.rename('old_name.txt', 'new_name.txt')

# Remove a file
os.remove('file_to_remove.txt')

# Get file size
size = os.path.getsize('example.txt')
print("File Size:", size, "bytes")
```

### Environment Variables
```python
# Get environment variable
path_var = os.environ.get('PATH')
print("PATH Variable:", path_var)

# Set environment variable
os.environ['MY_VAR'] = '123'
```

### Path Information
```python
# Split path into directory and file
path, file = os.path.split('/path/to/file.txt')
print("Path:", path, "File:", file)

# Get file extension
_, ext = os.path.splitext('example.txt')
print("Extension:", ext)
```

---

# Pathlib Module

### Basics
```python
from pathlib import Path

# Create a Path object
path = Path('.')

# Get current directory
print("Current Directory:", path.resolve())

# Check if a path exists
print("Exists:", path.exists())
```

### Directory Operations
```python
# Create a directory
Path('new_directory').mkdir()

# Remove a directory
Path('new_directory').rmdir()

# List files and directories
for item in path.iterdir():
    print(item)
```

### File Operations
```python
# Create a file
file_path = Path('example.txt')
file_path.touch()

# Write to a file
file_path.write_text("Hello, World!")

# Read from a file
content = file_path.read_text()
print("Content:", content)

# Remove a file
file_path.unlink()
```

### Path Information
```python
file_path = Path('/path/to/file.txt')

# Get parent directory
print("Parent Directory:", file_path.parent)

# Get file name
print("File Name:", file_path.name)

# Get file extension
print("File Extension:", file_path.suffix)

# Check if it's a file or directory
print("Is File:", file_path.is_file())
print("Is Directory:", file_path.is_dir())
```

### Advanced Operations
```python
# Join paths
new_path = file_path.parent / 'new_file.txt'
print("New Path:", new_path)

# Check if path is absolute
print("Is Absolute:", file_path.is_absolute())

# Glob for specific patterns
for txt_file in path.glob('*.txt'):
    print("Text File:", txt_file)

# Recursive glob
for py_file in path.rglob('*.py'):
    print("Python File:", py_file)

```



---

# Regix


# Python Cheatsheet: re Module

## Importing the `re` Module
```python
import re
```

## Basic Functions

### `re.match`
Matches a pattern only at the beginning of the string.
```python
pattern = r'\d+'
result = re.match(pattern, '123abc456')
if result:
    print("Match:", result.group())
else:
    print("No match")
```

#### Example: Match an Email Address
```python
pattern = r'[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}'

# Valid email
result = re.match(pattern, 'test.email@example.com')
if result:
    print("Valid Email:", result.group())

# Invalid email (does not start with an email pattern)
result = re.match(pattern, 'Hello test.email@example.com')
if result:
    print("Valid Email:", result.group())
else:
    print("No match")
```

#### Example: Match a URL
```python
pattern = r'https?://[a-zA-Z0-9.-]+(?:\.[a-zA-Z]{2,})+(/\S*)?'

# Valid URL
result = re.match(pattern, 'https://www.example.com/path')
if result:
    print("Valid URL:", result.group())

# Invalid URL
result = re.match(pattern, 'www.example.com')
if result:
    print("Valid URL:", result.group())
else:
    print("No match")
```

#### Example: Match a Date (YYYY-MM-DD)
```python
pattern = r'\d{4}-\d{2}-\d{2}'

# Valid date
result = re.match(pattern, '2024-12-20')
if result:
    print("Valid Date:", result.group())

# Invalid date
result = re.match(pattern, '20-12-2024')
if result:
    print("Valid Date:", result.group())
else:
    print("No match")
```

#### Example: Match a Phone Number (US Format)
```python
pattern = r'\(\d{3}\) \d{3}-\d{4}'

# Valid phone number
result = re.match(pattern, '(123) 456-7890')
if result:
    print("Valid Phone Number:", result.group())

# Invalid phone number
result = re.match(pattern, '123-456-7890')
if result:
    print("Valid Phone Number:", result.group())
else:
    print("No match")
```

---

## `re.search`
Searches for the first occurrence of the pattern in the string.
```python
pattern = r'\d+'
result = re.search(pattern, 'abc123xyz')
if result:
    print("Search Result:", result.group())
```

### `re.findall`
Finds all occurrences of the pattern in the string and returns them as a list.
```python
pattern = r'\d+'
results = re.findall(pattern, 'abc123xyz456')
print("Find All:", results)
```

### `re.finditer`
Finds all occurrences of the pattern and returns an iterator of match objects.
```python
pattern = r'\d+'
results = re.finditer(pattern, 'abc123xyz456')
for match in results:
    print("Match:", match.group())
```

### `re.split`
Splits the string at each match of the pattern.
```python
pattern = r',\s*'
result = re.split(pattern, 'apple, banana, cherry')
print("Split Result:", result)
```

### `re.sub`
Replaces matches of the pattern with a specified replacement.
```python
pattern = r'\d+'
replacement = '#'
result = re.sub(pattern, replacement, 'abc123xyz456')
print("Substitution Result:", result)
```

### `re.subn`
Similar to `re.sub` but also returns the number of substitutions made.
```python
pattern = r'\d+'
replacement = '#'
result, count = re.subn(pattern, replacement, 'abc123xyz456')
print("Substitution Result:", result, "Count:", count)
```

---

## Compiling Regular Expressions

### `re.compile`
Pre-compiles a regex pattern for repeated use.
```python
pattern = re.compile(r'\d+')
result = pattern.search('abc123xyz')
if result:
    print("Compiled Search Result:", result.group())
```

---

## Match Object Methods

### `group`
Returns the matched text.
```python
result = re.search(r'\d+', 'abc123xyz')
if result:
    print("Group:", result.group())
```

### `start` and `end`
Returns the start and end positions of the match.
```python
if result:
    print("Start:", result.start(), "End:", result.end())
```

### `span`
Returns a tuple of the start and end positions.
```python
if result:
    print("Span:", result.span())
```

---

## Special Sequences and Character Classes

### Special Sequences
- `\d` - Matches any digit (0-9).
- `\D` - Matches any non-digit.
- `\w` - Matches any word character (alphanumeric + underscore).
- `\W` - Matches any non-word character.
- `\s` - Matches any whitespace character.
- `\S` - Matches any non-whitespace character.

Example:
```python
pattern = r'\w+'
result = re.findall(pattern, 'Hello, World! 123')
print("Words:", result)
```

### Character Classes
- `[abc]` - Matches any of a, b, or c.
- `[^abc]` - Matches any character except a, b, or c.
- `[a-z]` - Matches any lowercase letter.

Example:
```python
pattern = r'[a-z]'
result = re.findall(pattern, 'ABCabc123')
print("Lowercase Letters:", result)
```

---

## Quantifiers

- `*` - Matches 0 or more repetitions.
- `+` - Matches 1 or more repetitions.
- `?` - Matches 0 or 1 repetition.
- `{n}` - Matches exactly n repetitions.
- `{n,}` - Matches n or more repetitions.
- `{n,m}` - Matches between n and m repetitions.

Example:
```python
pattern = r'\d{2,4}'
result = re.findall(pattern, '123 4567 89')
print("Digits:", result)
```

---

## Flags

### Common Flags
- `re.IGNORECASE` (`re.I`) - Makes the pattern case-insensitive.
- `re.MULTILINE` (`re.M`) - Allows `^` and `$` to match at the start and end of each line.
- `re.DOTALL` (`re.S`) - Allows `.` to match newlines as well.

Example:
```python
pattern = r'hello'
result = re.search(pattern, 'Hello World', re.IGNORECASE)
if result:
    print("Ignore Case Match:", result.group())
```

---

## Escaping Special Characters

Use `\` to escape special regex characters.
```python
pattern = r'\(.*?\)'
result = re.findall(pattern, '(abc) (def)')
print("Escaped Characters:", result)
```

