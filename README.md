
# **Regex Helper Library Documentation**

## **Overview**

The **Regex Helper Library** is designed to assist developers in working with regular expressions by providing a simple interface for matching, optimizing, explaining, and validating regex patterns. The library also includes a repository of commonly used regex patterns for various objects like email addresses, phone numbers, URLs, and more.

---

## **Core Components**

### 1. **RegexMatcher**
The **RegexMatcher** is the core component for performing regex operations. It allows users to match patterns, find all matches, and replace text based on patterns.

#### Methods:
- **`match(pattern: str, text: str) -> List[str]`**
  - **Description**: Matches the regex pattern against the given text and returns a list of all matches.
  - **Parameters**:
    - `pattern`: A string containing the regex pattern.
    - `text`: A string to match the pattern against.
  - **Returns**: A list of strings containing all matches.
  
- **`find_all(pattern: str, text: str) -> List[str]`**
  - **Description**: Finds all occurrences of the pattern in the text and returns them as a list.
  
- **`replace(pattern: str, text: str, replacement: str) -> str`**
  - **Description**: Replaces all occurrences of the pattern in the text with the given replacement.
  - **Parameters**:
    - `pattern`: The regex pattern.
    - `text`: The input text.
    - `replacement`: The replacement string for matched patterns.
  - **Returns**: The modified text after replacement.

### 2. **RegexOptimizer**
The **RegexOptimizer** class helps optimize slow or inefficient regex patterns, improving their performance, especially for large datasets.

#### Methods:
- **`optimize(pattern: str) -> str`**
  - **Description**: Returns an optimized version of the regex pattern.
  - **Parameters**:
    - `pattern`: The regex pattern to optimize.
  - **Returns**: The optimized regex pattern.
  
- **`simplify(pattern: str) -> str`**
  - **Description**: Simplifies complex regex patterns to more efficient versions.

### 3. **RegexExplanation**
The **RegexExplanation** class helps explain what a regex pattern does, making it easier for developers to understand complex patterns.

#### Methods:
- **`explain(pattern: str) -> str`**
  - **Description**: Provides a human-readable explanation of the regex pattern.
  - **Parameters**:
    - `pattern`: The regex pattern to explain.
  - **Returns**: A string containing the explanation of the pattern.

### 4. **RegexValidator**
The **RegexValidator** class is used to validate regex patterns to ensure they are correct and well-formed.

#### Methods:
- **`validate(pattern: str) -> bool`**
  - **Description**: Validates the syntax of the given regex pattern.
  - **Parameters**:
    - `pattern`: The regex pattern to validate.
  - **Returns**: `True` if the pattern is valid, `False` otherwise.

- **`validate_and_explain(pattern: str) -> str`**
  - **Description**: Validates the pattern and provides an explanation if there are any errors.
  - **Parameters**:
    - `pattern`: The regex pattern to validate.
  - **Returns**: An explanation of the pattern or an error message.

### 5. **RegexRepository**
The **RegexRepository** provides a collection of common regex patterns for objects like emails, phone numbers, URLs, and more. This allows developers to quickly access common regex patterns without having to search for them online.

#### Methods:
- **`get_pattern(name: str) -> str`**
  - **Description**: Retrieves the regex pattern for a specific object (e.g., email, phone).
  - **Parameters**:
    - `name`: The name of the pattern to retrieve (e.g., "email").
  - **Returns**: The regex pattern for the requested object.

- **`add_pattern(name: str, pattern: str)`**
  - **Description**: Adds a new custom regex pattern to the repository.
  - **Parameters**:
    - `name`: The name of the custom pattern.
    - `pattern`: The regex pattern.
  
- **`list_patterns() -> List[str]`**
  - **Description**: Lists all the available pre-built regex patterns.
  - **Returns**: A list of pattern names available in the repository.

---

## **CLI Tool**

The CLI tool allows developers to easily interact with the **Regex Helper Library** from the terminal. Here are the commands and their functionalities:

- **`regex-helper match <pattern> <text>`**
  - Matches the given regex pattern against the provided text.
  
- **`regex-helper replace <pattern> <text> <replacement>`**
  - Replaces all occurrences of the regex pattern in the text with the specified replacement.
  
- **`regex-helper optimize <pattern>`**
  - Optimizes the given regex pattern for better performance.
  
- **`regex-helper explain <pattern>`**
  - Provides an explanation of the given regex pattern.
  
- **`regex-helper validate <pattern>`**
  - Validates the given regex pattern.
  
- **`regex-helper list`**
  - Lists all available regex patterns in the repository.
  
- **`regex-helper add <name> <pattern>`**
  - Adds a custom regex pattern to the repository.

---

## **Example Usage**

### 1. **Using the Library in Code**

```python
from regex_helper import RegexMatcher, RegexRepository

# Create a RegexMatcher instance
matcher = RegexMatcher()
matches = matcher.match(r"\d{3}-\d{2}-\d{4}", "My SSN is 123-45-6789")
print(matches)  # Output: ['123-45-6789']

# Create a RegexRepository instance
repo = RegexRepository()

# Get a common regex pattern for email
email_pattern = repo.get_pattern('email')
print(email_pattern)  # Output: ^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$

# List all available patterns in the repository
patterns = repo.list_patterns()
print(patterns)  # Output: ['email', 'phone', 'url', 'date', 'ip', 'postal_code']
```

### 2. **CLI Usage**

- Match a regex pattern:
  ```bash
  regex-helper match "\d{3}-\d{2}-\d{4}" "My SSN is 123-45-6789"
  ```
  Output: `['123-45-6789']`

- Replace occurrences of a pattern:
  ```bash
  regex-helper replace "\d{3}-\d{2}-\d{4}" "My SSN is 123-45-6789" "XXX-XX-XXXX"
  ```
  Output: `"My SSN is XXX-XX-XXXX"`

- List all available patterns:
  ```bash
  regex-helper list
  ```
  Output: `['email', 'phone', 'url', 'date', 'ip', 'postal_code']`

---

## **Development Guidelines**

### **Code Structure**
- **regex_helper.py**: Main library file that contains classes for **RegexMatcher**, **RegexOptimizer**, **RegexExplanation**, **RegexValidator**, and **RegexRepository**.
- **cli.py**: CLI interface to interact with the library from the command line.
- **tests/**: Unit tests for all methods to ensure correctness.

### **Error Handling**
- Ensure that the library provides clear error messages for invalid regex patterns, mismatched types, and incorrect function usage.
- Implement proper exception handling for invalid user inputs in CLI commands.

### **Performance Considerations**
- Optimize regex matching, especially for large datasets or complex patterns.
- Optimize memory usage and ensure that large datasets do not cause memory overflow or excessive processing time.

### **Documentation and Help**
- Provide inline documentation for each method.
- The CLI should have a `--help` option to show users how to use the library and available commands.

---

## **Conclusion**
This Regex Helper Library aims to simplify and enhance the experience of working with regular expressions. By providing common patterns, optimization features, and explanations, your library will save developers time and reduce the complexity of regex-related tasks.

---
