#### php-learn
# ` <?php ?>`

## output
- `print`  has return value
- `echo`  no return value

## string
- `strrev`		reverse
- `str_word_count`    word
- `strlen`		string length


## replace
- `str_replace("a" ,"b" , "c")` replace a to b from c  

## var_dump($x)    
- `is_int`
- `is_float`
- `is_double`
- `is_infinate`
- `is_finate`
- `is_nan()`
- `acos()`  Invalid calculation will return a NaN value

- `is_numeric()` return bool if numeric

## function
- `function name(){}`


## global
- `global`
- ` $GLOBALS['y']` pick global $y 

## get min/max/positive
- `min(0, 150, 30, 20, -8, -200)` returns -200
- `max(0, 150, 30, 20, -8, -200)` returns 150
- `abs(-6.7)` return 6.7
- `sqrt(64)` square root return 8
- `round()` round
- `rand()`

## Operators
- `===`	*Identity*
	`$x === $y`	Returns true if have the same key/value pairs in the same order and types
- `!==` *Non-identity*
- `<=>` return integer less than 

## Array
- `array("Volvo", "BMW", "Toyota")` *key = array(values)*
ex) 
```php
#define array
<?php
$cars = array("Volvo", "BMW", "Toyota");
echo "I like " . $cars[0] . ", " . $cars[1] . " and " . $cars[2] . ".";
?>

# loop throgh arr
<?php
$cars = array("Volvo", "BMW", "Toyota");
$arrlength = count($cars);

for($x = 0; $x < $arrlength; $x++) {
  echo $cars[$x];
  echo "<br>";
}
?>
```
- arr defination other way
```
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

or

$age['Peter'] = "35";
$age['Ben'] = "37";
$age['Joe'] = "43";
```
*sample code)*
```php
<?php
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
echo "Peter is " . $age['Peter'] . " years old.";

# loop throgh
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

foreach($age as $x => $x_value) {
  echo "Key=" . $x . ", Value=" . $x_value;
  echo "<br>";
}

?>
```
- `Two-dimensional Arrays`
```php
<?php

echo $cars[0][0].": In stock: ".$cars[0][1].", sold: ".$cars[0][2].".<br>";
echo $cars[1][0].": In stock: ".$cars[1][1].", sold: ".$cars[1][2].".<br>";
echo $cars[2][0].": In stock: ".$cars[2][1].", sold: ".$cars[2][2].".<br>";
echo $cars[3][0].": In stock: ".$cars[3][1].", sold: ".$cars[3][2].".<br>";

for ($row = 0; $row < 4; $row++) {
  echo "<p><b>Row number $row</b></p>";
  echo "<ul>";
  for ($col = 0; $col < 3; $col++) {
    echo "<li>".$cars[$row][$col]."</li>";
  }
  echo "</ul>";
}

?>

```
- **sort**
  - `sort()`  asc order
  - `rsort()` desc order
  - `asort()` associative arrays in asc order, according to the value
  - `ksort()` associative arrays in asc order, according to the **key**
  - `arsort()` associative arrays in desc order, according to the value
  - `krsort()` associative arrays in desc order, according to the **key**


## code example
### condition
**if-else**
```php 
<?php
$t = date("H");

if ($t < "10") {
  echo "Have a good morning!";
} elseif ($t < "20") {
  echo "Have a good day!";
} else {
  echo "Have a good night!";
}
?>
 ```
---
**switch**
```php 
<?php

switch ($favcolor) {
  case "red":
    echo "Your favorite color is red!";
    break;
  case "blue":
    echo "Your favorite color is blue!";
    break;
  case "green":
    echo "Your favorite color is green!";
    break;
  default:
    echo "Your favorite color is neither red, blue, nor green!";
}

?>
 ```
---

### Constants are glob
## GLOBAL VAR
- `$GLOBALS`
- `$_SERVER` https://www.w3schools.com/php/php_superglobals_server.asp
- `$_REQUEST` $_REQUEST["email"] 
- `$_POST` $_POST["email"] 
- `$_GET` $_GET["email"]

_ex) used at form_
`<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>">`

 **exploits can be avoided by using htmlspecialchars()** 
 ```php
<?php
// define variables and set to empty values
$nameErr = $emailErr = $genderErr = $websiteErr = "";
$name = $email = $gender = $comment = $website = "";

if ($_SERVER["REQUEST_METHOD"] == "POST") {
  if (empty($_POST["name"])) {
    $nameErr = "Name is required";
  } else {
    $name = test_input($_POST["name"]);
  }
  
  if (empty($_POST["email"])) {
    $emailErr = "Email is required";
  } else {
    $email = test_input($_POST["email"]);
  }
    
  if (empty($_POST["website"])) {
    $website = "";
  } else {
    $website = test_input($_POST["website"]);
  }

  if (empty($_POST["comment"])) {
    $comment = "";
  } else {
    $comment = test_input($_POST["comment"]);
  }

  if (empty($_POST["gender"])) {
    $genderErr = "Gender is required";
  } else {
    $gender = test_input($_POST["gender"]);
  }
}
// 인풋값 
function test_input($data) {
  $data = trim($data);
  $data = stripslashes($data);
  $data = htmlspecialchars($data);
  return $data;
}
?>s
 ```

- `$_FILES`
- `$_ENV`
- `$_COOKIE`
- `$_SESSION`


```php 
<?php
define("cars", [
  "Alfa Romeo",
  "BMW",
  "Toyota"
]);
echo cars[0];
?>
 ```
---

```php 
<?php
// case-sensitive constant name
define("GREETING", "Welcome to W3Schools.com!");
echo GREETING;
?> 
 ```

### loops
**while**
```php 
<?php
$x = 1;

while($x <= 5) {
  echo "The number is: $x <br>";
  $x++;
}


$x = 1;

do {
  echo "The number is: $x <br>";
  $x++;
} while ($x <= 5);

for ($x = 0; $x <= 10; $x++) {
  echo "The number is: $x <br>";
}

$colors = array("red", "green", "blue", "yellow");

foreach ($colors as $value) {
  echo "$value <br>";
}

?>
 ```


## functions
```php 
<?php
function writeMsg() {
  echo "Hello world!";
}

writeMsg(); // call the function

// -------

function familyName($fname) {
  echo "$fname Refsnes.<br>";
}

familyName("Jani");
familyName("Hege");
familyName("Stale");
familyName("Kai Jim");
familyName("Borge");


// -------

function familyName($fname, $year) {
  echo "$fname Refsnes. Born in $year <br>";
}

familyName("Hege", "1975");
familyName("Stale", "1978");
familyName("Kai Jim", "1983");

?>
 ```
 #### its loosely typed Lang
```php 
<?php

function addNumbers(int $a, int $b) {
  return $a + $b;
}
echo addNumbers(5, "5 days");
// since strict is NOT enabled "5 days" is changed to int(5), and it will return 10

#--------
 declare(strict_types=1); // strict requirement

function addNumbers(int $a, int $b) {
  return $a + $b;
}
echo addNumbers(5, "5 days");
// since strict is enabled and "5 days" is not an integer, an error will be thrown

?>
 ```
 #### defualt argument val
```php 
<?php
declare(strict_types=1); // strict requirement
function setHeight(int $minheight = 50) { # default value
  echo "The height is : $minheight <br>";
  # to return value simplt add return statement below
  # return 1; 
}

setHeight(350);
setHeight(); // will use the default value of 50
setHeight(135);
setHeight(80);


# return type declartion   function name() : type {}
function addNumbers(float $a, float $b) : float {
  return $a + $b;
}
echo addNumbers(1.2, 5.2);
?>
 ```


## _Validate 정규식으로 검사_
- name 
```php
$name = test_input($_POST["name"]);
if (!preg_match("/^[a-zA-Z ]*$/",$name)) {
  $nameErr = "Only letters and white space allowed";
}
```
- email
```php
$email = test_input($_POST["email"]);
if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
  $emailErr = "Invalid email format";
}
```
- URL
```php
$website = test_input($_POST["website"]);
if (!preg_match("/\b(?:(?:https?|ftp):\/\/|www\.)[-a-z0-9+&@#\/%?=~_|!:,.;]*[-a-z0-9+&@#\/%=~_|]/i",$website)) {
  $websiteErr = "Invalid URL";
}
```

##### keep values in from `value="<?php echo $name;?>">`

## DATE FORMAT
```php
<?php
echo "Today is " . date("Y/m/d") . "<br>";
echo "Today is " . date("Y.m.d") . "<br>";
echo "Today is " . date("Y-m-d") . "<br>";
echo "Today is " . date("l");

# automatic copyright year
&copy; 2010-<?php echo date("Y");?>
# get curr time
echo "The time is " . date("h:i:sa");
# get my timezone
date_default_timezone_set("America/New_York");
echo "The time is " . date("h:i:sa");

# mktime  (January 1 1970 00:00:00 GMT)
$d=mktime(11, 14, 54, 8, 12, 2014);
echo "Created date is " . date("Y-m-d h:i:sa", $d);

# strtotime (readable to unix time)
$d=strtotime("10:30pm April 15 2014");
echo "Created date is " . date("Y-m-d h:i:sa", $d);


# 응용
$d=strtotime("tomorrow");
echo date("Y-m-d h:i:sa", $d) . "<br>";

$d=strtotime("next Saturday");
echo date("Y-m-d h:i:sa", $d) . "<br>";

$d=strtotime("+3 Months");
echo date("Y-m-d h:i:sa", $d) . "<br>";
?>
```
## __construct, __destruct
```php
class Fruit {
  public $name;
  public $color;

  function __construct($name, $color) {
    $this->name = $name;
    $this->color = $color;
  }
  function __destruct() {
    echo "The fruit is {$this->name} and the color is {$this->color}.";
  }

  protected function set_color($n) {
    $this->color = $n;
  }
  function get_name() {
    return $this->name;
  }

```


### _FRAMEWORKS_
- [ ] `Laravel`
- [ ] `CI(CodeIgniter)`
