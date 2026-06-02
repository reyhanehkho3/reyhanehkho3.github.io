---
title: PHP
publish: true
date created: 2026-06-03
---
## Structure and variables

- Every piece of PHP code must live inside PHP tags. 
```php
<?php
// PHP code goes here
?>
```

- Variables are case sensitive.
- Functions and keywords are not case sensitive.
- For displaying texts: 
```php
<?php
echo "Hello, World!";
?>
```

You can also use `print`. `echo` is more common.
- Variables start with a dollar sign. No need declaring the type. 
```php
$name = "Alex";
```
- Use a `.` to concate Strings.
```php
$firstName = "John";
$lastName = "Doe";

// Outputs: John Doe
echo $firstName . " " . $lastName;
```
- *Variable parsing*: Using double quotes(""), php automatically swap out variables for their values right inside the stirng.
```php
// Outputs: Hello Alex, you are 28.
echo "Hello $name, you are $age.";
```

## If/Else
same as java. Standard I guess.
```php
$score = 85;

if ($score >= 90) {
    echo "You got an A!";
} elseif ($score >= 80) {
    echo "You got a B!";
} else {
    echo "Keep studying!";
}
```

## Arrays
```php
// An indexed array
$fruits = ["Apple", "Banana", "Orange"];
echo $fruits[1]; // Outputs: Banana

// An associative array (key-value pairs)
$user = [
    "username" => "dev_mind",
    "email" => "alex@example.com"
];
echo $user["username"]; // Outputs: dev_mind
```

## Functions

Defined using `function` keyword.
```php
function greetUser($userName) {
    return "Welcome back, " . $userName . "!";
}

// Calling the function
echo greetUser("Sarah");
```

## PHP with HTML
PHP is a server-side language, so we can drop it right into our HTML structure.
```html
<!DOCTYPE html>
<html>
<body>

    <h1>Welcome to My Site</h1>
    <p>Today's date is <?php echo date('Y-m-d'); ?></p>

</body>
</html>
```