# Reflection – Static Code Analysis

## 1. What did you learn from using static code analysis tools?

I learned how static code analysis tools help identify code-quality problems, programming mistakes, security risks, and formatting violations without requiring manual inspection of every line. Pylint checks code quality, Bandit identifies potential security issues, and Flake8 checks coding style.

## 2. Which tool was most useful, and why?

Bandit was particularly useful because it identified potential security issues, including weak MD5 hashing and the use of `subprocess` with `shell=True`. These findings helped me understand the importance of avoiding unsafe shell commands and handling hashing functions appropriately.

## 3. What was the most important issue you fixed?

The most important issue was the use of `subprocess.call()` with `shell=True`, which could expose the program to command-injection risks. I replaced it with Python's `shutil.copy2()` function to perform file copying without executing a shell command.

## 4. How did the code change after applying the fixes?

I improved function and variable naming, added docstrings, corrected exception handling, removed the mutable default argument, specified file encodings, corrected formatting, and addressed the security warnings. These changes improved readability and maintainability while preserving the program's expected demonstration output.

## 5. How did you verify the improvements?

I reran Pylint, Bandit, and Flake8 after making the changes. Pylint reported a score of 10.00/10, Bandit reported no issues identified, and Flake8 produced an empty report. I also executed the Python program and confirmed that its output matched the expected output.
