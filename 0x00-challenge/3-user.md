# Python User Class - Issue and Fix

## Introduction

The Python User class is designed to model a user with a unique ID and a hashed password. The class includes methods for setting and validating passwords.

## Issue in Original Implementation

The original implementation had two main issues:

1. In the `password` setter method, the hashed password was being incorrectly stored in a new attribute `_password` instead of the intended private attribute `__password`.

    **Problematic Line:**
    ```python
    self._password = hashlib.md5(pwd.encode()).hexdigest().lower()
    ```

2. In the `is_valid_password` method, the hashed password was being converted to uppercase before comparison, which led to a mismatch since `__password` was stored in lowercase.

    **Problematic Line:**
    ```python
    return hashlib.md5(pwd.encode()).hexdigest().upper() == self.__password
    ```

## Fix

1. The fix for the first issue is to correctly update the `__password` attribute in the `password` setter method.

    **Corrected Line:**
    ```python
    self.__password = hashlib.md5(pwd.encode()).hexdigest().lower()
    ```

2. The fix for the second issue is to keep the hash in lowercase during the comparison in `is_valid_password`.

    **Corrected Line:**
    ```python
    return hashlib.md5(pwd.encode()).hexdigest().lower() == self.__password
    ```

## Corrected Code

Here's the corrected code snippet for the `password` setter and `is_valid_password` methods:

```python
@password.setter
def password(self, pwd):
    if pwd is None or type(pwd) is not str:
        self.__password = None
    else:
        self.__password = hashlib.md5(pwd.encode()).hexdigest().lower()

def is_valid_password(self, pwd):
    if pwd is None or type(pwd) is not str:
        return False
    if self.__password is None:
        return False
    return hashlib.md5(pwd.encode()).hexdigest().lower() == self.__password
```

## Conclusion

By correcting the attribute name in the `password` setter and maintaining consistent casing in the `is_valid_password` method, the Python User class now works as expected.