# Static Code Analysis – Issues Documentation

## Project: Vehicle Service Management System

### 1. Issues Identified and Proposed Fixes

| Issue | Type | Line(s) | Description | Fix Approach |
|---|---|---|---|---|
| Weak MD5 hash | Security – High | 39 | Bandit flagged MD5 as a weak hashing algorithm. | Set `usedforsecurity=False` because the hash is used only to generate a vehicle identifier, not for security. |
| Unsafe subprocess call | Security – High | 61 | Using `subprocess.call()` with `shell=True` may allow command injection. | Replace the subprocess command with Python's `shutil.copy2()`. |
| Mutable default argument | Code Quality | 12 | The default list `history=[]` may be shared across function calls. | Use `None` as the default and create a new list inside the function. |
| Broad exception handling | Code Quality | 23 | Catching `Exception` may hide unexpected errors. | Catch the specific `KeyError` exception. |
| Hardcoded password | Security – Low | 8 | The password `garage-demo` is directly stored in the source code. | Remove the unused `ADMIN_PASSWORD` constant. |
| Missing module docstring | Code Quality | 1 | The module lacks a description of its purpose. | Add a module-level docstring. |
| Missing function docstrings | Code Quality | Multiple | Functions do not document their purpose. | Add descriptive docstrings to the functions. |
| Incorrect naming conventions | Code Quality | Multiple | Function names and variables use camelCase instead of snake_case. | Rename identifiers using snake_case. |
| Missing file encoding | Code Quality | 50, 55 | File operations do not explicitly specify an encoding. | Add `encoding="utf-8"` to file-opening operations. |
| Missing whitespace after comma | Code Style | 7 | Flake8 detected a missing space after a comma. | Add the required whitespace. |
| Missing whitespace around operator | Code Style | 43 | Flake8 detected incorrect spacing around an assignment operator. | Add the required spaces around the operator. |
| Incorrect blank-line spacing | Code Style | 49 | Flake8 detected insufficient blank lines before a function definition. | Add the required blank lines. |
| Line exceeds maximum length | Code Style | 77 | Flake8 detected a line exceeding the 79-character limit. | Split the long line across multiple lines. |
| Unnecessary subprocess import | Code Quality | 3 | The program imports `subprocess` for a file-copy operation. | Remove the import and use `shutil` instead. |

### 2. Additional Improvements

- Added an `if __name__ == "__main__":` guard.
- Added UTF-8 encoding when reading and writing JSON files.
- Improved code readability through consistent formatting and naming.
- Preserved the original service rates and demonstration behavior.

### 3. Validation

The updated program was executed successfully, and its output matched the original expected output.

The following tools will be used to validate the changes:

- **Pylint:** Checks code quality and programming conventions.
- **Bandit:** Identifies potential security issues.
- **Flake8:** Checks code style and formatting.

The final reports will be reviewed to determine which issues were resolved and whether any warnings remain.

### 4. Final Validation Results

| Tool | Initial Findings | Final Findings | Result |
|---|---|---|---|
| Pylint | Multiple code-quality warnings; rating 4.66/10 | No issues; rating 10.00/10 | Passed |
| Bandit | 4 potential security issues | No issues identified | Passed |
| Flake8 | 4 style violations | No violations reported | Passed |

### 5. Conclusion

Static code analysis helped identify and resolve code-quality, security, and formatting issues in the Vehicle Service Management System.

The mutable default argument was corrected, broad exception handling was replaced with specific exception handling, and unsafe shell-based file copying was replaced with Python's `shutil` module.

The final program executed successfully and preserved the expected demonstration output. The final Pylint, Bandit, and Flake8 reports showed no issues.
