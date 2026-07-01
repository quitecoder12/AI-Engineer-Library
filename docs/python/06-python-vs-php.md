# Python vs PHP

> A guide for PHP developers transitioning to Python

---

# Variables

PHP

```php
$name = "Ajit";
```

Python

```python
name = "Ajit"
```

---

# Arrays

PHP

```php
$numbers = [1,2,3];
```

Python

```python
numbers = [1,2,3]
```

---

# Associative Arrays

PHP

```php
$user = [
    "name"=>"Ajit",
    "age"=>50
];
```

Python

```python
user = {
    "name":"Ajit",
    "age":50
}
```

---

# foreach

PHP

```php
foreach($users as $user){
}
```

Python

```python
for user in users:
    pass
```

---

# Function

PHP

```php
function hello(){

}
```

Python

```python
def hello():
    pass
```

---

# Class

PHP

```php
class User{

}
```

Python

```python
class User:

    pass
```

---

# Null

PHP

```php
null
```

Python

```python
None
```

---

# Boolean

| PHP | Python |
|------|---------|
| true | True |
| false | False |

---

# Include

PHP

```php
require_once "db.php";
```

Python

```python
import db
```

---

# Semicolon

PHP

```php
echo "Hello";
```

Python

```python
print("Hello")
```

Python does not require semicolons.

---

# Curly Braces

PHP

```php
if($x){

}
```

Python

```python
if x:
    pass
```

Indentation replaces braces.

---

# Final Advice

Don't try to write Python like PHP.

Learn Python's style and idioms. Doing so will make your code simpler, more readable, and more aligned with the broader Python ecosystem.
