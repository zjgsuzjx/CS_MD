> 💥此MD/PDF/HTML文档由 [@竹梦者也 ](https://www.zjgsuzjx.top/)编辑制作，不可贩卖❌。仅供学习交流使用，下载后切勿随意传播。转载麻烦加上出处~
>
> 📌欢迎在留言区提供修改建议~
>
> 💌本文内容和代码来自于西兰花老师的AJAX教程
>
> 
>
> ✅2021.7.6	 @竹梦者也(https://www.zjgsuzjx.top) 
>
> 💡2021.7.10	V1.1（完善了部分知识体系）







## 一、PHP基础

### 一、PHP基本语法

#### 1. 初识PHP

PHP 脚本可以放在文档中的任何位置。

PHP 脚本以 **<?php** 开始，以 **?>** 结束：

```php
<?php
// PHP 代码
?>
```

- PHP 文件的默认文件扩展名是 ".php"。
- PHP 文件通常包含 `HTML` 标签和一些 `PHP` 脚本代码。
- PHP 中的每个代码行都必须以**分号**结束。分号是一种分隔符，用于把指令集区分开来。
- 通过 PHP，有两种在浏览器输出文本的基础指令：`echo` 和 `print`。

**简单输出**：

```php
<?php
echo "Hello World!";
?>
```

#### 2. PHP 中的注释

```php
<?php
// 这是 PHP 单行注释

/*
这是
PHP 多行
注释
*/
?>
```

#### 3. PHP变量

**PHP 变量规则**：

- 变量以 `$` 符号开始，后面跟着变量的名称
- 变量名必须以字母或者下划线字符开始
- 变量名只能包含字母数字字符以及下划线（A-z、0-9 和 _ ）
- 变量名不能包含空格
- 变量名是**区分大小写**的（$y 和 $Y 是两个不同的变量）

```php
<?php
$x = 5;
$y = 6;
$z = $x + $y;
echo $z;
?>
```

> 注释：PHP 变量名称对大小写敏感！

PHP 没有创建变量的命令。变量会在首次为其赋值时被创建。

```php
<?php
$txt = "Hello world!";
$x = 5;
$y = 10.5;
?>
```

> 注释：如果您为变量赋的值是文本，请用引号包围该值。

**PHP 变量作用域**：

在 PHP 中，可以在脚本的任意位置对变量进行声明。

变量的作用域指的是变量能够被引用/使用的那部分脚本。

PHP 有三种不同的变量作用域：

- `local`（局部）
- `global`（全局）
- `static`（静态）

函数*之外*声明的变量拥有 `Global` 作用域，只能在**函数以外**进行访问。

函数*内部*声明的变量拥有 `LOCAL` 作用域，只能在**函数内部**进行访问。

```php
<?php
$x=5; // 全局作用域

function myTest() {
    $y=10; // 局部作用域
    echo "<p>测试函数内部的变量：</p>";
    echo "变量 x 是：$x";	// 报错
    echo "<br>";
    echo "变量 y 是：$y";	// 10
}

myTest();

echo "<p>测试函数之外的变量：</p>";
echo "变量 x 是：$x";	// 5
echo "<br>";
echo "变量 y 是：$y";	// 报错
?>
```

**global 关键词**：

`global` 关键词用于在<u>函数内访问全局变量</u>。

要做到这一点，请在（函数内部）变量前面使用 `global` 关键词：

```php
<?php
$x=5;
$y=10;

function myTest() {
    global $x,$y;
    $y=$x+$y;
}

myTest();
echo $y; // 输出 15
?>
```

#### 4. 输出语句

在 PHP 中，有两种基本的输出方法：`echo` 和 `print`。

`echo` 和 `print` 之间的**差异**：

- `echo` - 能够输出一个以上的字符串
- `print` - 只能输出一个字符串，并始终返回 1

> 提示：echo 比 print 稍快，因为它不返回任何值。

**echo 语句**：

echo 是一个语言结构，有无括号均可使用：`echo` 或 `echo()`。

下面的例子展示如何用 `echo` 命令来显示不同的字符串（<u>同时请注意字符串中能包含 `HTML` 标记</u>）：

```php
<?php
echo "<h2>PHP is fun!</h2>";
echo "Hello world!<br>";
echo "I'm about to learn PHP!<br>";
echo "This", " string", " was", " made", " with multiple parameters.";
?>
```

输出结果为：

<img src="https://img.zjgsuzjx.top/img/images/2021/06/30/e5faff204dc94d95681e8ed4f6dcbd58.jpg" alt="e5faff204dc94d95681e8ed4f6dcbd58.jpg" border="0" />

参杂变量的语法：

```php
<?php
$txt1="Learn PHP";
$txt2="W3School.com.cn";
$cars=array("Volvo","BMW","SAAB");

echo $txt1;
echo "<br>";
echo "Study PHP at $txt2";
echo "My car is a {$cars[0]}";
?>
```

**print 语句**：

`print` 也是语言结构，有无括号均可使用：`print` 或 `print()`。

> 把上面的代码换成 `print` 就可以了。

#### 5. PHP 数据类型

字符串、整数、浮点数、逻辑、数组、对象、NULL。

**字符串**：

字符串可以是引号内的任何文本。您可以使用**单引号**或**双引号**。

**整数**：

整数规则：

- 整数必须有至少一个数字（0-9）
- 整数不能包含逗号或空格
- 整数不能有小数点
- 整数正负均可
- 可以用三种格式规定整数：十进制、十六进制（前缀是 0x）或八进制（前缀是 0）

```php
<?php
$x = 5985;
var_dump($x);
echo "<br>";
$x = -345; // 负数
var_dump($x);
echo "<br>";
$x = 0x8C; // 十六进制数
var_dump($x);
echo "<br>";
$x = 047; // 八进制数
var_dump($x);
?>
```

> `var_dump()` 会返回变量的数据类型和值

**浮点数**：

```php
$x = 10.365;
echo "<br>";
$x = 2.4e3;
```

**逻辑**：

逻辑是 true 或 false。

```php
<?php
$x=true;
$y=false;
?>
```

**数组**：

```php
<?php
$cars=array("Volvo","BMW","SAAB");
var_dump($cars);
?>
```

**对象**：

在 PHP 中，必须明确地声明对象。对此，我们使用 `class` 关键词。类是包含属性和方法的结构。

然后我们在对象类中定义数据类型，然后在该类的实例中使用此数据类型：

```php
<?php
class Car
{
    var $color;
    function Car($color="green") {
        $this->color = $color;
    }
    function what_color() {
        return $this->color;
    }
}
?>
```

**NULL 值**：

特殊的 `NULL` 值表示变量无值。`NULL` 是数据类型 `NULL` 唯一可能的值。

> `NULL` 值标示变量是否为空。也用于区分空字符串与空值数据库。

可以通过把值设置为 `NULL`，将变量清空：

```php
<?php
$x="Hello world!";
$x=null;
var_dump($x);
?>
```

#### 6. 字符串函数

**strlen() 函数**：

strlen() 函数返回字符串的长度，以字符计。

```php
<?php
echo strlen("Hello world!");	// 12
?>
```

**单词计数**：
`str_word_count()` 函数对字符串中的单词进行计数：

```php
<?php
echo str_word_count("Hello world!"); // 输出 2
?>
```

**反转字符串**：

`strrev()` 函数反转字符串：

```php
<?php
echo strrev("Hello world!"); // 输出 !dlrow olleH
?>
```

**strpos() 函数**：

`strpos()` 函数用于检索字符串内指定的字符或文本。

如果找到匹配，则会返回首个匹配的字符位置。如果未找到匹配，则将返回 `FALSE`。

```php
<?php
echo strpos("Hello world!","world"); // 6
?>
```

> 提示：上例中字符串 "world" 的位置是 6。是 6（而不是 7）的理由是，字符串中首字符的位置是 0 而不是 1。

**替换字符串中的文本**：

`str_replace()` 函数用一些字符串替换字符串中的另一些字符。

```php
<?php
echo str_replace("world", "Kitty", "Hello world!"); // 输出 Hello Kitty!
?>
```

#### 7. 常量

> 常量类似变量，但是常量一旦被定义就无法更改或撤销定义。

常量是单个值的标识符（名称）。在脚本中无法改变该值。

有效的常量名以字符或下划线开头（常量名称前面没有 `$` 符号）。

> 注释：与变量不同，常量贯穿整个脚本是自动全局的。

**设置 PHP 常量**：

如需设置常量，请使用 `define()` 函数 - 它使用三个参数：

1. 首个参数定义常量的名称
2. 第二个参数定义常量的值
3. 可选的第三个参数规定常量名是否对大小写不敏感。默认是 `false`。

```php
<?php
define("GREETING", "Welcome to W3School.com.cn!");
echo GREETING;
?>
```

常量是**自动全局**的，而且可以贯穿整个脚本使用。

下面的例子在函数内使用了一个常量，即使它在函数外定义：

```php
<?php
define("GREETING", "Welcome to W3School.com.cn!");

function myTest() {
    echo GREETING;
}

myTest();
?>
```

#### 8. PHP 运算符

**算数运算符**：

```php
<?php
$x=17;
$y=8;
echo ($x + $y); // 输出 25
echo ($x - $y); // 输出 9
echo ($x * $y); // 输出 136
echo ($x / $y); // 输出 2.125
echo ($x % $y); // 输出 1
?>
```

**赋值运算符**：

PHP 中基础的赋值运算符是 "`=`"。这意味着右侧赋值表达式会为左侧运算数设置值。

```php
<?php
$x=17;
echo $x; // 输出 17
$y=17;
$y += 8;
echo $y; // 输出 25
$z=17;
$z -= 8;
echo $z; // 输出 9
$i=17;
$i *= 8;
echo $i; // 输出 136
$j=17;
$j /= 8;
echo $j; // 输出 2.125
$k=17;
$k %= 8;
echo $k; // 输出 1
?>
```

**字符串运算符**：

```php
<?php
$a = "Hello";
$b = $a . " world!";
echo $b; // 输出 Hello world!

$x="Hello";
$x .= " world!";
echo $x; // 输出 Hello world!
?>
```

> 相当于JS里的`+`

**递增/递减运算符**：

```php
<?php
$x=17;
echo ++$x; // 输出 18

$y=17;
echo $y++; // 输出 17

$z=17;
echo --$z; // 输出 16

$i=17;
echo $i--; // 输出 17
?>
```

**比较运算符**：

| 运算符 | 名称               | 例子      | 结果                                               |
| :----- | :----------------- | :-------- | :------------------------------------------------- |
| ==     | 等于               | $x == $y  | 如果 $x 等于 $y，则返回 true。                     |
| ===    | 全等（完全相同）   | $x === $y | 如果 $x 等于 $y，且它们类型相同，则返回 true。     |
| !=     | 不等于             | $x != $y  | 如果 $x 不等于 $y，则返回 true。                   |
| <>     | 不等于             | $x <> $y  | 如果 $x 不等于 $y，则返回 true。                   |
| !==    | 不全等（完全不同） | $x !== $y | 如果 $x 不等于 $y，或它们类型不相同，则返回 true。 |
| >      | 大于               | $x > $y   | 如果 $x 大于 $y，则返回 true。                     |
| <      | 小于               | $x < $y   | 如果 $x 小于 $y，则返回 true。                     |
| >=     | 大于或等于         | $x >= $y  | 如果 $x 大于或者等于 $y，则返回 true.              |
| <=     | 小于或等于         | $x <= $y  | 如果 $x 小于或者等于 $y，则返回 true。             |

**逻辑运算符**：

| 运算符 | 名称 | 例子       | 结果                                             |
| :----- | :--- | :--------- | :----------------------------------------------- |
| and    | 与   | $x and $y  | 如果 $x 和 $y 都为 true，则返回 true。           |
| or     | 或   | $x or $y   | 如果 $x 和 $y 至少有一个为 true，则返回 true。   |
| xor    | 异或 | $x xor $y  | 如果 $x 和 $y 有且仅有一个为 true，则返回 true。 |
| &&     | 与   | $x && $y   | 如果 $x 和 $y 都为 true，则返回 true。           |
| \|\|   | 或   | $x \|\| $y | 如果 $x 和 $y 至少有一个为 true，则返回 true。   |
| !      | 非   | !$x        | 如果 $x 不为 true，则返回 true。                 |

**数组运算符**：

| 运算符 | 名称   | 例子      | 结果                                                         |
| :----- | :----- | :-------- | :----------------------------------------------------------- |
| +      | 联合   | $x + $y   | $x 和 $y 的联合（但不覆盖重复的键）                          |
| ==     | 相等   | $x == $y  | 如果 $x 和 $y 拥有相同的键/值对，则返回 true。               |
| ===    | 全等   | $x === $y | 如果 $x 和 $y 拥有相同的键/值对，且顺序相同类型相同，则返回 true。 |
| !=     | 不相等 | $x != $y  | 如果 $x 不等于 $y，则返回 true。                             |
| <>     | 不相等 | $x <> $y  | 如果 $x 不等于 $y，则返回 true。                             |
| !==    | 不全等 | $x !== $y | 如果 $x 与 $y 完全不同，则返回 true。                        |

### 二、PHP逻辑语法

#### 1. 条件语句

在 PHP 中，我们可以使用以下条件语句：

- *if 语句* - 如果指定条件为真，则执行代码
- *if...else 语句* - 如果条件为 `true`，则执行代码；如果条件为 `false`，则执行另一端代码
- *if...elseif....else 语句* - 根据两个以上的条件执行不同的代码块
- *switch 语句* - 选择多个代码块之一来执行

##### 1.1 if 语句

```
if (条件) {
当条件为 true 时执行的代码;
}

if (条件) {
  条件为 true 时执行的代码;
} else {
  条件为 false 时执行的代码;
}

if (条件) {
  条件为 true 时执行的代码;
} elseif (condition) {
  条件为 true 时执行的代码;
} else {
  条件为 false 时执行的代码;
}
```

下例将输出 "Have a good day!"，如果当前时间 (HOUR) 小于 20：

```php
<?php
$t=date("H");

if ($t<"20") {
    echo "Have a good day!";
}
?>
```

如果当前时间 (HOUR) 小于 20，下例将输出 "Have a good day!"，否则输出 "Have a good night!"：

```php
<?php
$t=date("H");

if ($t<"20") {
    echo "Have a good day!";
} else {
    echo "Have a good night!";
}
?>
```

如果当前时间 (HOUR) 小于 10，下例将输出 "Have a good morning!"，如果当前时间小于 20，则输出 "Have a good day!"。否则将输出 "Have a good night!"：

```php
<?php
$t=date("H");

if ($t<"10") {
    echo "Have a good morning!";
} elseif ($t<"20") {
    echo "Have a good day!";
} else {
    echo "Have a good night!";
}
?>
```

##### 1.2 Switch 语句

使用 `Switch` 语句可以避免冗长的 `if..elseif..else` 代码块。

```
switch (expression){
case label1:
	expression = label1 时执行的代码 ;
	break;
case label2:
	expression = label2 时执行的代码 ;
	break;
default:
	表达式的值不等于 label1 及 label2 时执行的代码;
}
```

**工作原理**：

1. 对表达式（通常是变量）进行一次计算
2. 把表达式的值与结构中 `case` 的值进行比较
3. 如果存在匹配，则执行与 `case` 关联的代码
4. 代码执行后，*`break` 语句*阻止代码跳入下一个 `case` 中继续执行
5. 如果没有 `case` 为真，则使用 `default` 语句

```php
<?php
$favfruit="orange";

switch ($favfruit) {
    case "apple":
        echo "Your favorite fruit is apple!";
        break;
    case "banana":
        echo "Your favorite fruit is banana!";
        break;
    case "orange":
        echo "Your favorite fruit is orange!";
        break;
    default:
        echo "Your favorite fruit is neither apple, banana, or orange!";
}
?>
```

#### 2. 循环语法

在 PHP 中，我们有以下循环语句：

- *`while`* - 只要指定条件为真，则循环代码块
- *`do...while`* - 先执行一次代码块，然后只要指定条件为真则重复循环
- *`for`* - 循环代码块指定次数
- *`foreach`* - 遍历数组中的每个元素并循环代码块

##### 2.1 while 循环

```
while (条件为真) {
    要执行的代码;
}
```

```php
<?php
$x=1;

while($x<=5) {
    echo "这个数字是：$x <br>";
    $x++;
}
?>
```

##### 2.2 do...while 循环

`do...while` 循环首先会执行一次代码块，然后检查条件，如果指定条件为真，则重复循环。

```
do {
    要执行的代码;
} while (条件为真);
```

```php
<?php
$x=1;

do {
    echo "这个数字是：$x <br>";
    $x++;
} while ($x<=5);
?>
```

> 请注意，`do while` 循环只在执行循环内的语句之后才对条件进行测试。这意味着 `do while` 循环至少会执行一次语句，即使条件测试在第一次就失败了。

##### 2.3 for 循环

如果您已经提前确定脚本运行的次数，可以使用 for 循环。

```
for (init counter; test counter; increment counter) {
    code to be executed;
}
```

参数：

- `init counter`：初始化循环计数器的值
- `test counter`：: 评估每个循环迭代。如果值为 TRUE，继续循环。如果它的值为 FALSE，循环结束。
- `increment counter`：增加循环计数器的值

```php
<?php
for ($x=0; $x<=10; $x++) {
    echo "数字是：$x <br>";
}
?>
```

##### 2.4 foreach 循环

foreach 循环只适用于**数组**，并用于遍历数组中的每个键/值对。

```
foreach ($array as $value) {
    code to be executed;
}
```

> 每进行一次循环迭代，当前数组元素的值就会被赋值给 `$value` 变量，并且数组指针会逐一地移动，直到到达最后一个数组元素。

下面的例子演示的循环将输出给定数组（$colors）的值：

```php
<?php
$colors = array("red","green","blue","yellow");

foreach ($colors as $value) {
    echo "$value <br>";
}
?>
```

### 三、PHP函数

> PHP是世界上最好的语言。	------匿名

它拥有超过 4000 个内建的函数。

#### 1. 用户定义函数

页面加载时函数不会立即执行。函数只有在被调用时才会执行。

用户定义的函数声明以单词 "`function`" 开头：

```
function functionName() {
    被执行的代码;
}
```

> 注释：函数名能够以字母或下划线开头（而非数字）。

> 注释：函数名对大小写不敏感。

> 提示：函数名应该能够反映函数所执行的任务。最好用驼峰命名法。

```php
<?php
function sayHi() {
    echo "Hello world!";
}

sayhi(); // 调用函数
?>
```

#### 2. 函数参数

可以通过参数向函数传递信息。参数类似变量。参数被定义在函数名之后，括号内部。您可以添加任意多参数，只要用**逗号**隔开即可。

```php
<?php
function familyName($fname) { // 一个参数
    echo "$fname Zhang.<br>";
}

familyName("Li");
familyName("Hong");
familyName("Tao");
familyName("Xiao Mei");
familyName("Jian");
?>
    
<?php
function familyName($fname,$year) { // 多个参数
  echo "$fname Zhang. Born in $year <br>";
}

familyName("Li","1975");
familyName("Hong","1978");
familyName("Tao","1983");
?>
```

#### 3. 默认参数值

下面的例子展示了如何使用默认参数。如果我们调用没有参数的 `setHeight()` 函数，它的参数会取默认值：

```php
<?php
function setHeight($minheight=50) {
    echo "The height is : $minheight <br>";
}

setHeight(350);
setHeight(); // 将使用默认值 50
setHeight(135);
setHeight(80);
?>
```

#### 4. 返回值

如需使函数返回值，请使用 `return` 语句：

```php
<?php
function sum($x,$y) {
  $z=$x+$y;
  return $z;
}

echo "5 + 10 = " . sum(5,10) . "<br>";
echo "7 + 13 = " . sum(7,13) . "<br>";
echo "2 + 4 = " . sum(2,4);
?>
```

### 四、数组

#### 1. 创建数组

在 PHP 中， `array()` 函数用于创建数组：

```
array();
```

在 PHP 中，有三种数组类型：

- *索引数组* - 带有数字索引的数组
- *关联数组* - 带有指定键的数组
- *多维数组* - 包含一个或多个数组的数组（暂时不学）

#### 2. 索引数组

有两种创建索引数组的方法：（索引是自动分配的，索引从 0 开始）

```php
$cars=array("porsche","BMW","Volvo");
```

或者也可以手动分配索引：

```php
$cars[0]="porsche";
$cars[1]="BMW";
$cars[2]="Volvo";
```

**遍历索引数组**：

`count()` 函数用于返回数组的长度（元素数）。

```php
<?php
$cars=array("porsche","BMW","Volvo");
$arrlength=count($cars);

for($x=0;$x<$arrlength;$x++) {
    echo $cars[$x];
    echo "<br>";
}
?>
```

#### 3. 关联数组

> 关联数组是使用你分配给数组的指定键的数组。类似JS的对象。

有两种创建关联数组的方法：

```php
$age=array("Bill"=>"35","Steve"=>"37","Elon"=>"43");
```

或者：

```php
$age['Bill']="63";
$age['Steve']="56";
$age['Elon']="47";
```

**具体应用**：

```php
<?php
$age=array("Bill"=>"63","Steve"=>"56","Elon"=>"47");
echo "Elon is " . $age['Elon'] . " years old.";
?>
```

**遍历关联数组**：

如需遍历并输出关联数组的所有值，可以使用 `foreach` 循环，就像这样：

```php
<?php
$age=array("Bill"=>"63","Steve"=>"56","Elon"=>"47");

foreach($age as $x=>$x_value) {
    echo "Key=" . $x . ", Value=" . $x_value;
    echo "<br>";
}
?>
```

#### 4. 数组排序

主要有如下 PHP 数组排序函数：

- sort() - 以升序对数组排序
- rsort() - 以降序对数组排序
- asort() - 根据值，以升序对关联数组进行排序
- ksort() - 根据键，以升序对关联数组进行排序
- arsort() - 根据值，以降序对关联数组进行排序
- krsort() - 根据键，以降序对关联数组进行排序

**sort()**：

下面的例子按照**字母升序**对数组 $cars 中的元素进行排序：

```php
<?php
$cars=array("porsche","BMW","Volvo");
sort($cars);
?>
```

**asort()**：

下面的例子根据**值**对**关联数组**进行升序排序：

```php
<?php
$age=array("Bill"=>"63","Steve"=>"56","Elon"=>"47");
asort($age);
// Key=Elon, Value=47；Key=Steve, Value=56；Key=Bill, Value=63
?>
```

**ksort()**：

下面的例子根据键对关联数组进行升序排序：

```php
<?php
$age=array("Bill"=>"63","Steve"=>"56","Elon"=>"47");
ksort($age);
// Key=Bill, Value=63Key=Elon, Value=47Key=Steve, Value=56
?>
```

### 五、超全局

> 超全局变量在 PHP 4.1.0 中引入，是在全部作用域中始终可用的内置变量。和JS中的`window`相似。

PHP 中的许多预定义变量都是“超全局的”，这意味着它们在一个脚本的全部作用域中都可用。在函数或方法中无需执行 <u>`global` `$variable`</u>; 就可以访问它们。

这些超全局变量是：

- $GLOBALS
- $_SERVER
- $_REQUEST
- $_POST
- $_GET
- $_FILES
- $_ENV
- $_COOKIE
- $_SESSION

#### 1. $GLOBALS

> 引用全局作用域中可用的全部变量。

$GLOBALS 这种全局变量用于在 PHP 脚本中的任意位置访问全局变量（从**函数**或**方法**中均可）。

PHP 在名为 `$GLOBALS[index]` 的数组中存储了所有全局变量。变量的名字就是数组的键。

```php
<?php
$x = 75;
$y = 25;

function addition() {
    $GLOBALS['z'] = $GLOBALS['x'] + $GLOBALS['y'];
}

addition();
echo $z; // 100
?>
```

> 在上面的例子中，由于 `z` 是 `$GLOBALS` 数组中的变量，因此在函数之外也可以访问它。

#### 2. $_SERVER

`$_SERVER` 这种超全局变量保存<u>关于报头、路径和脚本位置的信息</u>。

下面的例子展示了如何使用 `$_SERVER` 中的某些元素：

```php
<?php
echo $_SERVER['PHP_SELF'];
echo "<br>";
echo $_SERVER['SERVER_NAME'];
echo "<br>";
echo $_SERVER['HTTP_HOST'];
echo "<br>";
echo $_SERVER['HTTP_REFERER'];
echo "<br>";
echo $_SERVER['HTTP_USER_AGENT'];
echo "<br>";
echo $_SERVER['SCRIPT_NAME'];
?>
```

下表列出了您能够在 `$_SERVER` 中访问的最重要的元素：

| 元素/代码                       | 描述                                                         |
| :------------------------------ | :----------------------------------------------------------- |
| $_SERVER['PHP_SELF']            | 返回当前执行脚本的文件名。                                   |
| $_SERVER['GATEWAY_INTERFACE']   | 返回服务器使用的 CGI 规范的版本。                            |
| $_SERVER['SERVER_ADDR']         | 返回当前运行脚本所在的服务器的 IP 地址。                     |
| $_SERVER['SERVER_NAME']         | 返回当前运行脚本所在的服务器的主机名（比如 www.zjgsuzjx.top）。 |
| $_SERVER['SERVER_SOFTWARE']     | 返回服务器标识字符串（比如 Apache/2.2.24）。                 |
| $_SERVER['SERVER_PROTOCOL']     | 返回请求页面时通信协议的名称和版本（例如，“HTTP/1.0”）。     |
| $_SERVER['REQUEST_METHOD']      | 返回访问页面使用的请求方法（例如 POST）。                    |
| $_SERVER['REQUEST_TIME']        | 返回请求开始时的时间戳（例如 1577687494）。                  |
| $_SERVER['QUERY_STRING']        | 返回查询字符串，如果是通过查询字符串访问此页面。             |
| $_SERVER['HTTP_ACCEPT']         | 返回来自当前请求的请求头。                                   |
| $_SERVER['HTTP_ACCEPT_CHARSET'] | 返回来自当前请求的 Accept_Charset 头（ 例如 utf-8,ISO-8859-1） |
| $_SERVER['HTTP_HOST']           | 返回来自当前请求的 Host 头。                                 |
| $_SERVER['HTTP_REFERER']        | 返回当前页面的完整 URL（不可靠，因为不是所有用户代理都支持）。 |
| $_SERVER['HTTPS']               | 是否通过安全 HTTP 协议查询脚本。                             |
| $_SERVER['REMOTE_ADDR']         | 返回浏览当前页面的用户的 IP 地址。                           |
| $_SERVER['REMOTE_HOST']         | 返回浏览当前页面的用户的主机名。                             |
| $_SERVER['REMOTE_PORT']         | 返回用户机器上连接到 Web 服务器所使用的端口号。              |
| $_SERVER['SCRIPT_FILENAME']     | 返回当前执行脚本的绝对路径。                                 |
| $_SERVER['SERVER_ADMIN']        | 该值指明了 Apache 服务器配置文件中的 SERVER_ADMIN 参数。     |
| $_SERVER['SERVER_PORT']         | Web 服务器使用的端口。默认值为 “80”。                        |
| $_SERVER['SERVER_SIGNATURE']    | 返回服务器版本和虚拟主机名。                                 |
| $_SERVER['PATH_TRANSLATED']     | 当前脚本所在文件系统（非文档根目录）的基本路径。             |
| $_SERVER['SCRIPT_NAME']         | 返回当前脚本的路径。                                         |
| $_SERVER['SCRIPT_URI']          | 返回当前页面的 URI。                                         |

#### 3. $_REQUEST

`$_REQUEST` 用于收集 HTML 表单提交的数据。

下面的例子展示了一个包含输入字段及提交按钮的表单。当用户通过点击提交按钮来提交表单数据时, 表单数据将发送到 `<form>` 标签的 `action` 属性中指定的脚本文件。在这个例子中，我们<u>指定文件本身来处理表单数据</u>。如果您需要使用其他的 PHP 文件来处理表单数据，请修改为您选择的文件名即可。然后，我们可以使用超级全局变量 `$_REQUEST` 来收集 input 字段的值：

```php+HTML
<form method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
    Name: <input type="text" name="fname">
    <input type="submit">
</form>

<?php
$name = $_REQUEST['fname'];
echo $name;
?>
```

#### 4. $_POST

`$_POST` 广泛用于收集提交 `method="post"` 的 HTML 表单后的表单数据。`$_POST` 也常用于传递变量。

> 例子同上一个相同。

#### 6. $_GET

`$_GET` 也可用于收集提交 HTML 表单 (`method="get"`) 之后的表单数据。

`$_GET` 也可以收集 `URL` 中的发送的数据。

假设我们有一张页面含有带参数的超链接：

```html
<html>
<body>

<a href="test_get.php?subject=PHP&web=zjgsuzjx.top">测试 $GET</a>

</body>
</html>
```

当用户点击链接 "测试 $GET"，参数 "subject" 和 "web" 被发送到 "test_get.php"，然后您就能够通过 $_GET 在 "test_get.php" 中访问这些值了。

下面的例子是 "test_get.php" 中的代码：

```php
<?php
echo "在 " . $_GET['web'] . " 学习 " . $_GET['subject'];
?>
```

### 六、PHP 表单

> 这个章节很重要，已经涉及到AJAX基础。这里简单学习一下就好啦。

#### 表单处理

PHP 超全局变量 `$_GET` 和 `$_POST` 用于收集**表单数据**（form-data）。

- 表单`name`属性的是用来提供给服务端接收所传递数据而设置的
- 表单`action`属性设置接收数据的处理程序
- 表单`method`属性设置发送数据的方式
- 当上传文件是需要设置 `enctype="multipart/form-data"`，且只能`post`方式

- `$_GET`接收 `get` 传值
- `$_POST`接收 `post` 传值
- `$_FILES`接收文件上传

**简单的 HTML 表单**：

下面的例子显示了一个简单的 HTML 表单，它包含两个输入字段和一个提交按钮：

```html
<html>
<body>

<form action="welcome.php" method="post">
    Name: <input type="text" name="name"><br>
    E-mail: <input type="text" name="email"><br>
    <input type="submit">
</form>

</body>
</html>
```

当用户填写此表单并点击提交按钮后，表单数据会发送到名为 `"welcome.php"` 的 PHP 文件供处理。表单数据是通过 `HTTP POST` 方法发送的。

如需显示出被提交的数据，您可以简单地输出（`echo`）所有变量。"`welcome.php`" 文件是这样的：

```php+HTML
<html>
<body>

Welcome <?php echo $_POST["name"]; ?><br>
Your email address is: <?php echo $_POST["email"]; ?>

</body>
</html>
```

> 使用 HTTP GET 方法也能得到相同的结果

**get和post的区别**：

- `Get`是**不安全**的，因为在传输过程，数据被放在请求的URL中；`Post`的所有操作对用户来说都是**不可见**的。
- `Get`传送的数据量**较小**，这主要是因为受URL长度限制；`Post`传送的数据量较大，一般被默认为**不受限制**。
- `Get`限制Form表单的数据集的值必须为`ASCII`字符；而`Post`支持整个ISO10646字符集。
- `Get`执行效率却比`Post`方法**好**。`Get`是`form`提交的默认方法。
- `Get`由于变量显示在 URL 中，把页面添加到书签中也更为方便；`Post`由于变量未显示在 URL 中，也就无法将页面添加到书签。

> 注意：绝不能使用 `GET` 来发送密码或其他敏感信息！

### 七、PHP高级

#### 1. Include 文件

`include` （或 `require`）语句会获取指定文件中存在的所有文本/代码/标记，并复制到使用 `include` 语句的文件中。

> include文件很有用，如果您需要在网站的多张页面上引用相同的 PHP、HTML 或文本的话。

**include 和 require 语句**：

通过 `include` 或 `require` 语句，可以将 PHP 文件的内容插入另一个 PHP 文件（**在服务器执行它之前**）。

**include 和 require 区别**：

- `require` 会生成致命错误（`E_COMPILE_ERROR`）并停止脚本
- `include` 只生成警告（`E_WARNING`），并且脚本会继续

比如：

```php
<?php
// include 'noFileExists.php';
// require 'noFileExists.php';
echo "I have a $color $car.";
?>
```

> 用require就不会出现`I have a` ，而include会出现。

因此，如果希望继续执行，并向用户输出结果，即使包含文件已丢失，那么请使用 `include`。否则，在框架、CMS 或者复杂的 PHP 应用程序编程中，请始终使用 `require` 向执行流引用关键文件。这有助于提高应用程序的安全性和完整性，在某个关键文件意外丢失的情况下。

**实例**：

假设我们有一个名为 "footer.php" 的标准的页脚文件，就像这样：

```php
<?php
echo "<p>Copyright © 2006-" . date("Y") . " zjgsuzjx.top</p>";
?>
```

如需在一张页面中引用这个页脚文件，请使用 include 语句：

```php+HTML
<html>
<body>

<h1>欢迎访问我们的首页！</h1>
<p>一段文本。</p>
<p>一段文本。</p>
<?php include 'footer.php';?>

</body>
</html>
```

也可以在调用文件中使用这些变量：

```php
<?php
$color='银色的';
$car='奔驰轿车';
?>
```

```php+HTML
<html>
<body>

<h1>欢迎访问我的首页！</h1>
<?php
include 'vars.php';
echo "我有一辆" . $color . $car "。";
?>

</body>
</html>
```

#### 2. 文件上传

**创建一个文件上传表单**：

`<form>` 标签的 `enctype` 属性规定了在提交表单时要使用哪种内容类型。在表单需要二进制数据时，比如文件内容，请使用 `"multipart/form-data"`。

`<input>` 标签的 `type="file"` 属性规定了应该把输入作为文件来处理。举例来说，当在浏览器中预览时，会看到输入框旁边有一个浏览按钮。

```html
<form action="upload_file.php" method="post"
      enctype="multipart/form-data">
    <label for="file">Filename:</label>
    <input type="file" name="file" id="file"/>
    <br/>
    <input type="submit" name="submit" value="Submit"/>
</form>
```

**保存被上传的文件**：

> 在服务器的 PHP 临时文件夹创建了一个被上传文件的临时副本。

这个临时的复制文件会在脚本结束时消失。要保存被上传的文件，我们需要把它拷贝到**另外的位置**：

```php
<?php
if (true) {
    if ($_FILES["file"]["error"] > 0) {
        echo "Return Code: " . $_FILES["file"]["error"] . "<br />";
    } else {
        echo "Upload: " . $_FILES["file"]["name"] . "<br />";
        echo "Type: " . $_FILES["file"]["type"] . "<br />";
        echo "Size: " . ($_FILES["file"]["size"] / 1024) . " Kb<br />";
        echo "Temp file: " . $_FILES["file"]["tmp_name"] . "<br />";

        if (file_exists("upload/" . $_FILES["file"]["name"])) {
            echo $_FILES["file"]["name"] . " already exists. ";
        } else {
            move_uploaded_file($_FILES["file"]["tmp_name"],
                "upload/" . $_FILES["file"]["name"]);
            echo "Stored in: " . "upload/" . $_FILES["file"]["name"];
        }
    }
} else {
    echo "Invalid file";
}
?>
```

上面的脚本检测了是否已存在此文件，如果不存在，则把文件拷贝到指定的文件夹。

> 注释：这个例子把文件保存到了名为 "upload" 的新文件夹。

## 二、网络传输协议

> 此章节为计算机网络部分概念基础，学过可以略过，也可以复习一下。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/01/a680144bbfff3d12766519e9327fc828.jpg" alt="a680144bbfff3d12766519e9327fc828.jpg" border="0" />

### 一、常见协议

1、HTTP、HTTPS 超文本传输协议

2、FTP 文件传输协议

3、SMTP 简单邮件传输协议

### 二、HTTP协议

即超文本传输协议，网站是基于`HTTP`协议的，例如网站的图片、CSS、JS等都是基于`HTTP`协议进行传输的。

`HTTP`协议（hypertext transport protocol）是由从客户机到服务器的请求(Request)和从服务器到客户机的响应(Response)进行了约束和规范。现在主流http2.0。

**特点**：无状态，现在cookie解决了无状态的问题（早期网页开发时，用cookie解决，现在是cookie和session配合使用）

即`HTTP`协议主要由请求和响应构成。

常用请求方法 `POST`、`GET`、`PUT`、`DELETE`

#### 1. 请求/请求报文

请求由客户端发起，其规范格式为：**请求行**、**请求头**、**请求主体**。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/01/fb60e6a70ffb0b59a4878594f2528310.png" alt="fb60e6a70ffb0b59a4878594f2528310.png" border="0" />

**请求行**：

由请求方式、请求URL和协议版本构成

**请求头**：

`Host`：localhost请求的目标主机（主机名:端口号）

`Cache`-`Control`：max-age=0控制缓存

`Accept`：`*/*` 接受的文档MIME类型

`User-Agent`：用户代理，判断用户浏览器版本**很重要**

`Referer`：从哪个`URL`跳转过来的（1.防盗链如微信 2.广告计费）

`Origin`：精简版的`Referer`

`Accept-Encoding`：可接受的压缩格式

`Upgrade-Insecure-Requests`：浏览器告诉服务器是否可以使用https

`DNT`：浏览器告诉服务器是否禁止跟踪。

`Cookie`：node里再将

`Content-Type`：浏览器告诉服务器，发送数据的类型

**请求主体**：

即传递给服务端的数据。

> 注：当以`post`形式提交表单的时候，请求头里会设置`Content-Type: application/x-www-form-urlencoded`，而`get`形式当不需要
>
> **备注**：
>
> `form`表单的 `post`请求和`get`请求，参数均已`urlencoded`形式进行编码
>
> `get`请求将`urlencoded`编码的参数放入请求地址携带给服务器，所以称之为：查询字符事参数。
>
> `post`请求将`urlencoded`编码的参数放入请求体，所以称之为：请求体参数。

#### 2. 响应/响应报文

响应由服务器发出，其规范格式为：**状态行**、**响应头**、**响应主体**。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/01/d3f5d45ddd897141e6a3101c6751bbfc.png" alt="d3f5d45ddd897141e6a3101c6751bbfc.png" border="0" />

**状态行**：

由协议版本号、状态码和状态信息构成。

**响应头**：

`Date`：响应时间

`Server`：服务器信息

`Content-Length`：返回数据的长度

`Content-Type`：响应资源的MIME类型

Connection：服务器告诉浏览器下次请求时或许会采用长连接

`X-Powered-By`：服务器所采用的框架（尽量不要让用户知道服务器采用的技术）

> `MIME`是标识文件类型的，文件后缀并不能正确无误的标识文件的类型。
>
> 可以禁止服务器返回`X-Powered-By`：
>
> `app.disable('x-powered-by')`

客户端与服务器在进行数据传输的时候都是以字节形式进行的，我们可以理解成是以“**文本形式**”传输，这时浏览器就需要明确知道该怎么样来解析这些文本形式的数据，`MIME`就是明确告知浏览器该如何来处理。

**响应主体**：

即服务端返回给客户端的内容。

<u>状态码分类</u>：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/01/5fcd45ac5efa959cbc5cd6ab9760d4cb.png" alt="5fcd45ac5efa959cbc5cd6ab9760d4cb.png" border="0" />

常见的有`200`代表成功、`304`文档未修改、`403`没有权限、`404`未找到、`500`服务器错误、`502`连接服务器失败。

`301`：重定向，被请求的旧资源永久移除了（不可以访问了），将会跳转到一个新资源，搜索引擎在抓取新内容的同时也将旧的网址替换为重定向之后的网址。

`302`：重定向，被请求的旧资源还在（仍然可以访问），但会临时跳转到一个新资源，搜索引擎会抓取新的内容而保存旧的网址。

> 推荐谷歌插件：http status

#### 3. 调试工具

利用HTTP抓包工具在开发中可以帮我们进行调试，常用抓包工具HttpWatch、`Fiddler`、`Charles`、FireBug等

**浏览器插件**：

Firebug、HttpWatch、chrome dev tools

**代理软件**：

Charles、Fiddler

> 浏览器的network是个好东西

### 三、网站解析过程

> 将域名翻译成IP地址。

#### 1. DNS解析步骤

1.找浏览器DNS缓存解析域名

2.找本机DNS缓存（备注：查看本机DNS缓存`cmd`命令：`ipconfig/displaydns > C:/dns.txt`）

3.找路由器DNS缓存

4.找运营商DNS缓存（80%的DNS查找，到这一步结束）

5.递归查询（查询全球13台根DNS服务器）

#### 2. 三次握手

进行TCP（协议）连接，三次握手（根据上一步请求回来的`ip`地址，去联系服务器）

**第一次提手**：由浏览器发给服务器，我想和你说话，你能“听见”嘛？

**第二次握手**：由服务器发给浏览器，我能听得见，你说吧！

**第三次握手**：由浏览器发给服务器，好，那我就开始说话。

#### 3. 浏览器解析HTML

1. 预解析：将所有外部的资源，发请求出去
2. 解析html，生成DOM树
3. 解析CSS，生成CSS树--合并成一个render树
4. JS是否操作了DOM或样式
   有：进行重绘或重排（不好，1.尽最避免；2.最小化重绘重排）没有：null
5. 最终展示界面

#### 4. 四次挥手

断开TCP连接，四次挥手（确保数拥的完整性）

第一次挥手：由浏览器发给服务器，我的东西接受完了，你断开心。

第二次挥手：由服务器发给到览器，我还有一些东西没接收完，你等一会，我接收好了我告诉你

第三次探手：由服务器发给浏览器，我接收完了，你断开吧

第四次挥手：由浏览器发给服务器，好的，那我断开了

> **备注**：为什么握手要三次，挥手要四次？
> 握手之前，还没有进行数据的运输，确认握手就可以了。
> 挥手之前，正在进行数据的传输，为了确保数据的完整性，必须多经历一次验证。

## 三、AJAX

AJAX = Asynchronous JavaScript and XML（异步的 JavaScript 和 XML）。

> AJAX 是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/01/0324d1605e43e405358b601f4a18f99e.jpg" alt="0324d1605e43e405358b601f4a18f99e.jpg" border="0" />

### 一、XHR

#### 1. 基本用法

```js
<script>
document.querySelector('input').onclick = function(){
        // 创建 对象 异步对象
        var xhr = new XMLHttpRequest();
        // 请求行
        xhr.open('get','xxx.php?name=jack&skill=painting');
        // 注册回调函数 请求响应回来之后触发
        xhr.onload = function(){
            console.log('请求响应回来啦');
            console.log(xhr.responseText);
            alert(xhr.responseText);
        }
        // 请求头 setRequestHeader get请求 可以省略 设置请求头的操作
        // xhr.setRequestHeader('heima','goodgoodstudy day day up');
        // 请求主体 发送
        xhr.send(null);
}
</script>
```

**1、创建异步对象**

```js
var xhr = new XMLHttpRequest();
```

**2、向服务器发送请求**

```js
xhr.open('get','xxx.php?name=jack&skill=painting');
```

| 方法                         | 描述                                                         |
| :--------------------------- | :----------------------------------------------------------- |
| open(*method*,*url*,*async*) | 规定请求的类型、URL 以及是否异步处理请求。*method*：请求的类型；GET 或 POST*url*：文件在服务器上的位置*async*：`true`（异步，默认）或 `false`（同步） |
| send(*string*)               | 将请求发送到服务器。*string*：仅用于 POST 请求               |

**`GET` 和 `POST`比较**：

与 POST 相比，GET 更简单也更快，并且在大部分情况下都能用。

然而，在以下情况中，请使用 POST 请求：

- 无法使用缓存文件（更新服务器上的文件或数据库）
- 向服务器发送大量数据（POST 没有数据量限制）
- 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠

如果需要像 `HTML` 表单那样 `POST` 数据，请使用 `setRequestHeader()` 来添加 `HTTP` 头。然后在 `send()` 方法中规定您希望发送的数据：

```js
<script>
    // 点击事件
    document.querySelector('input').onclick = function(){
        //1.创建对象
        var xhr = new XMLHttpRequest();
        //2.设置请求行(get请求数据写在url后面)
        xhr.open('post','postData.php');
        //3.设置请求头(get请求可以省略,post不发送数据也可以省略)
        // 可以在 w3c的 ajax分类中 w3c的 form表单的 enctype中 看到 这个值
        xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");
        //3.5注册回调函数
        xhr.onload = function(){
            console.log(xhr.responseText);
        }
        //4.请求主体发送(get请求为空，或者写null，post请求数据写在这里，如果没有数据，直接为空或者写null)
        // key=value&key2=value2
        xhr.send('name = 西兰花&friend = 鸡蛋');
    }
</script>
```

**3、服务器响应**

如需获得来自服务器的响应，请使用 XMLHttpRequest 对象的 responseText 或 responseXML 属性。

| 属性         | 描述                       |
| :----------- | :------------------------- |
| responseText | 获得字符串形式的响应数据。 |
| responseXML  | 获得 XML 形式的响应数据。  |

```js
xhr.status; // 状态码
xhr.statusText; // 状态信息
xhr.getResponseHeader('Content-Type'); // 获取指定头信息
xhr.getAllResponseHeaders(); // 获取所有响应头信息
```

**`GET` 和 `POST` 请求方式的差异**：

1、`GET`没有请求主体，使用`xhr.send(null)`

2、`GET`可以通过在请求URL上添加请求参数

3、`POST`可以通过`xhr.send('name=itcast&age=10')`

4、GET效率更好（应用多）

5、GET大小限制约4K，POST则没有限制

**服务器端**：

```php
<?php
    header('content-type:text/xml;charset=utf-8');
    $xmlString=file_get_contents('1.xml'); // 需要返回的数据文件
    echo $xmlString; // 返回的内容，必写
?>
```

#### 2. onreadystatechange 事件

> 是另一种回调函数注册方式。

| 属性               | 描述                                                         |
| :----------------- | :----------------------------------------------------------- |
| onreadystatechange | 存储函数（或函数名），每当 readyState 属性改变时，就会调用该函数。 |
| readyState         | 存有 XMLHttpRequest 的状态。从 0 到 4 发生变化。0: 请求未初始化1: 服务器连接已建立2: 请求已接收3: 请求处理中4: 请求已完成，且响应已就绪 |
| status             | 200: "OK"404: 未找到页面                                     |

在 `onreadystatechange` 事件中，我们规定当服务器响应已做好被处理的准备时所执行的任务。

```js
xhr.onreadystatechange = function () {
    if (xhr.readyState == 4 && xhr.status == 200) {
        console.log(xhr.responseText);
    }
}
```

> `onreadystatechange` 事件被触发 5 次（0 - 4），对应着 `readyState` 的每个变化。

#### 3. API

`API`（Application Programming Interface，应用程序接口）是一些预先定义的接口（如函数、HTTP接口），或指软件系统不同组成部分衔接的约定。

> 我的理解是相当于你编辑好了一个php文件，然后只要告诉别人你这个php文件的参数的格式及含义，就可以通过`get`或者`post`的方式来访问你的php文件，你的php文件得到发送过来的数据以后（可以是自定义链接的拼接，也可以是send的方式），就会返回给别人相应的数据。

**简单的API天气预报请求例子**：

```html
  /*
    点击按钮 -- 点击事件
    获取输入的城市 -- dom.value
    查询天气预报 -- ajax 调用接口
    数据回来之后 渲染到页面上 
      回调函数
  */
<script>
    document.querySelector('input[type=button]').onclick = function(){
        //1.创建异步对象
        var xhr= new XMLHttpRequest();
        //2.设置请求行
        // api 接口文档
        xhr.open('get', 'http://wthrcdn.etouch.cn/WeatherApi?city=' + document.querySelector('input[type=text]').value);
        //3.设置请求头(get请求可以省略)
        //4.注册状态改变事件
        xhr.onreadystatechange = function(){
            //4.1判断状态&请求是否成功并使用数据
            if(xhr.readyState == 4 && xhr.status==200){
                console.log(xhr.responseXML);
            }
        }
        //5.发送请求
        xhr.send(null);
    }
</script>
```

### 二、XML

> 如果需要得到数据量过大，就不便于解析；服务器返回的数据不会被切割（除非代码切割，但效率低下）。于是就有了XML。

#### 1. XML含义

- XML 指可扩展标记语言（*EX*tensible *M*arkup *L*anguage）
- XML 是一种*标记语言*，很类似 HTML
- XML 的设计宗旨是*传输数据*，而非显示数据
- XML 标签没有被预定义。您需要*自行定义标签*。
- XML 被设计为具有*自我描述性*。
- XML 是 *W3C 的推荐标准*

#### 2. XML用途

- 把数据从 HTML 分离
- 简化数据共享
- 简化数据传输
- 简化平台的变更
- 使数据更有用
- 用于创建新的 Internet 语言

#### 3. XML用法

**简单的例子**

**XML文件内容**：

```xml
<?xml version="1.0" encoding="utf-8"?> <!--必写-->
<bookstore><!--任意，必须是标签-->
<book category="COOKING">
  <title lang="en">Everyday Italian</title> 
  <author>Giada De Laurentiis</author> 
  <year>2005</year> 
  <price>30.00</price> 
</book>
<book category="CHILDREN">
  <title lang="en">Harry Potter</title> 
  <author>J K. Rowling</author> 
  <year>2005</year> 
  <price>29.99</price> 
</book>
<book category="WEB">
  <title lang="en">Learning XML</title> 
  <author>Erik T. Ray</author> 
  <year>2003</year> 
  <price>39.95</price> 
</book>
</bookstore>
```

**php文件内容**：

```php
<?php
    header('content-type:text/xml;charset=utf-8'); // 必写，声明用的是xml数据格式
    $xmlString=file_get_contents('1.xml');
    echo $xmlString; // 返回给html
?>
```

**html文件内容**：

```html
<input type="submit">
<h2></h2>
<script>
    document.querySelector('input').onclick = function () {
        var xhr = new XMLHttpRequest();
        xhr.open('get', 'getHeros.php');
        xhr.onreadystatechange = function () {
            if (xhr.readyState == 4 && xhr.status == 200) {
                // 解析 XML数据
                var allHero = xhr.responseXML.querySelectorAll('book');
                // 创建ul
                var ulDom = document.createElement('ul');
                // 添加到body中
                document.body.appendChild(ulDom);
                for (var i = 0; i < allHero.length; i++) {
                    var currentHero = allHero[i];
                    var icon = currentHero.querySelector('icon').innerHTML;
                    var name = currentHero.querySelector('name').innerHTML;
                    // 创建li
                    var liDom = document.createElement('li');
                    liDom.innerHTML = '<img src="' + icon + '">--<span>' + name + '</span>';
                    // 添加到ul中
                    ulDom.appendChild(liDom);
                }
            }
        }
        xhr.send(null);
    }
</script>
```

#### 4. 缺点

1、传输的数据量大（如今网速不是问题）

2、解析略微有点复杂（主要原因）

> 目前使用最频繁的是 `JSON`，`XML`基本碰不到。

### 三、JSON

`JSON`(JavaScript Object Notation, JS 对象简谱) 是一种轻量级的数据交换格式。易于人阅读和编写，同时也易于机器解析和生成，并有效地提升网络传输效率。

#### 1. 概念

- JSON是一种数据的格式
- JSON跟编程语言没有关系
- JSON的载体是字符串
- 基本上所有的编程语言都支持JSON
- 语法简洁、基本上所有的编程语言都提供了对应的方法来解析JSON
- JSON格式的字符串转化完毕之后会变成数组、对象

#### 2. 语法

**用来表示对象**：

```html
<script>
    // 对象使用 {} 
    // 属性名和属性值 必须使用 "" 包裹 如果属性值是数值 可以不使用双引号
    var JSONObject = '{"name":"刘亦菲","skill":"失忆"}';
    console.log(JSONObject);
    // 转化为 对应的 对象(数组)
    var obj = JSON.parse(JSONObject);
    console.log(obj);
    console.log(obj.name+'|'+obj.skill);
</script>
```

> 切记里面不能用单引号，因为外单内双原则。

**用来表示数组**：

```html
<script>
    var JSONArr = '["绿色的花菜","大蒜","大葱","番茄","圣女果"]';
    console.log(JSONArr);
    // 转化为 对应的 数组(对象)
    var arr = JSON.parse(JSONArr);
    console.log(arr);
    console.log(arr[2]);
</script>
```

**用来表示对象数组**：

```html
<script>
    var JSONObjArr = '{"name":"曹操","skill":"背叛","friends":["关羽","刘备","张飞"]}';
    console.log(JSONObjArr);
    // 转化为对应的 对象 数组
    var result = JSON.parse(JSONObjArr);
    console.log(result);
    console.log(result.runfriends[1]);
</script>
```

#### 3. 完整应用

**json文件内容**：

```json
[{
  "name": "吴京",
  "skill": "徒手抓狼"
},
  {
    "name": "吴彦祖",
    "skill": "帅气"
  },
  {
    "name": "张国荣",
    "skill": "霸王别姬"
  },
  {
    "name": "林俊杰",
    "skill": "小酒窝--美美哒"
  }
]
```

**php文件内容**：

```php
<?php
// JSON也要设置一段内容 (可选)
// 告诉浏览器 返回的是 JSON格式的数据 编码是 utf-8
header('content-type:application/json;charset=utf-8');

// 读取JSON文件
$jsonString = file_get_contents('data/stars.json');

// 返回读取的内容
echo $jsonString;
?>
```

**html文件内容**：

```html
<script>
    // 点击时候获取
    document.querySelector('input').onclick = function () {
        //1.创建异步对象
        var xhr = new XMLHttpRequest();
        //2.设置请求行
        xhr.open('post', 'backJSON.php');
        //3.设置请求头(get请求可以省略)
        //4.注册状态改变事件
        xhr.onreadystatechange = function () {
            //4.1判断状态&请求是否成功并使用数据
            if (xhr.readyState == 4 && xhr.status == 200) {
                // JSON的载体是字符串 用responseText 即可获取
                console.log(xhr.responseText);
                // 转化为 对应的 对象(数组)
                var arr = JSON.parse(xhr.responseText);
                console.log(arr);
                // 遍历打印
                for(var i =0;i<arr.length;i++){
                    var currentObj = arr[i];
                    console.log('姓名:'+currentObj.name+'  技能:'+currentObj.skill);
                }
            }
        }
        //5.发送请求
        xhr.send(null);
    }
</script>
```

#### 4. 获取网络上的JSON文件

以bilibili为例子：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/02/068d58ac40f46e975cbd41fc78d3ed0e.png" alt="068d58ac40f46e975cbd41fc78d3ed0e.png" border="0" />

> 一个小技巧：按文件大小降序，文件最大的数据量肯定也大。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/02/f8a52a68d8e418e2d760f257abf90796.png" alt="f8a52a68d8e418e2d760f257abf90796.png" border="0" />

#### 5. 案例

```js
<script>
    // 按数量随机刷新
    document.querySelector(".getData").onclick=function () {
        let xhr=new XMLHttpRequest();
        xhr.open('get', './api/HeroInfo_List_get.php?num=' + $('.heroNum').val());
        xhr.onreadystatechange = function () {
            if(xhr.status==200&&xhr.readyState==4){
                var $clone = $('.col-xs-4').first().clone(); // 克隆元素
                let obj=JSON.parse(xhr.responseText);
                document.querySelector('.row').innerHTML=""; // 克隆后删了刷新前的元素
                for(let i=0;i<obj.data.length;i++) {
                    let current = obj.data[i];
                    $clone.find('img').attr('src', current.champion_icon);
                    $clone.find('span').html(current.champion_name);
                    $('.row').append($clone);
                    $clone = $('.col-xs-4').first().clone();
                }
            }
        }
        xhr.send(null);
    }

    //模态框
    $('.row').on('click', 'a', function () { // 事物委托原理绑定事件
        var xhr = new XMLHttpRequest();
        xhr.open('post', './api/HeroInfo_details_post.php');
        xhr.setRequestHeader("Content-type", "application/x-www-form-urlencoded"); // 因为要传输数据，所以要请求头
        xhr.onreadystatechange = function () {
            if(xhr.readyState==4&&xhr.status==200){
                var dataObj = JSON.parse(xhr.responseText);
                // 修改模态框的信息
                $('.jumbotron').find('img').attr('src',dataObj.data.champion_icon);
                $('.jumbotron').find('p').first().html(dataObj.data.champion_tags);
                $('.jumbotron').find('p').last().html(dataObj.data.champion_info);
                $('.jumbotron').find('a').attr('href',dataObj.data.champion_url);
                // 弹出模态框，这是JQ的语法
                $('.modal').modal('show');
            }
        }
        xhr.send('name='+$(this).find('span').html()); // 传输对应的数据
    })
</script>
```

### 四、AJAX函数封装

> 为了能够便于其它开发者调用，专注于使用异步回来的数据，需要一个封装函数将get和post放在同一个JS文件内。

#### 1. get和post单独设置

```js
/**
 * ajax工具函数-get
 * @param {*} url
 * @param {*} data(key1=value1&key2=value2)
 * @param {*} success
 */
function get(url, data, success) {
    var xhr = new XMLHttpRequest();
    if (data) {
        url += '?';
        url += data;
    }
    xhr.open('get', url);
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            success(xhr.responseText);
        }
    }
    xhr.send(null);
}

/**
 * ajax工具函数-post
 * @param {*} url
 * @param {*} data (key1=value1&key2=value2)
 * @param {*} success
 */
function post(url, data, success) {
    var xhr = new XMLHttpRequest();
    xhr.open('post', url);
    if (data) {
        xhr.setRequestHeader('Content-type', 'application/x-www-form-urlencoded');
    }
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            console.log(xhr.responseText);
            success(xhr.responseText);
        }
    }
    xhr.send(data);
}
```

> 其中`success`是一个回调函数，用来接受异步回来的数据，把这个数据作为回调函数的参数返回给html页面。

**html页面的写法如下**：

```js
// get请求
document.querySelector('.get').onclick = function(){
    // 直接调用 get方法
    //function get(url, data, success)
    get('../00.backData/01.backSendData.php','name=jack&friend=rose',function(data){
        console.log(data);
    })
}

// post请求
document.querySelector('.post').onclick = function(){
    // 直接调用 get方法
    //function post(url, data, success)
    post('../00.backData/01.backSendData.php','name=rose&friend=青椒',function(data){
        alert(data);
    })
}
```

> 其中回调函数就是第三个参数`function`，`data`用来接受异步回来的数据，之后的操作全部写在回调函数中。

#### 2. post和get合写

> 将post和get函数合在一起写，可以减少代码量，需要再增添一个参数用来判断是哪个数据请求。

```js
/**
 * 参数越来越多之后 用户如果要传递参数 必须遵循
 * @param {*} url
 * @param {*} type
 * @param {*} data
 * @param {*} success
 */
function ajax_test(url, type, data, success) {
    var xhr = new XMLHttpRequest();
    // 如果是get 并且有数据
    if (type == 'get' && data) {
        url += '?';
        url += data;
        data = null; // 这样最后直接send data即可 
    }
    xhr.open(type, url);
    // post请求 并且有数据
    if (type == 'post' && data) {
        xhr.setRequestHeader('Content-type', 'application/x-www-form-urlencoded');
    }
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            success(xhr.responseText);
        }
    }
    xhr.send(data);
}
```

#### 3. 参数改为对象

> get和post函数内的参数可能会越来越多，不便于传递处理。可以统一放在一个对象内，通过对象名.属性名来调用。

**JS文件**：

```js
/*
    url
    type
    data
    success
*/
function ajax(option) {
    var xhr = new XMLHttpRequest();
    // 如果是get 并且有数据
    if (option.type == 'get' && option.data) {
        option.url += '?';
        option.url += option.data;
        option.data = null; // 这样最后直接send data即可 
    }
    xhr.open(option.type, option.url);
    // post请求 并且有数据
    if (option.type == 'post' && option.data) {
        xhr.setRequestHeader('Content-type', 'application/x-www-form-urlencoded');
    }
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
            var type = xhr.getResponseHeader('Content-Type');
            // 是否为json
            if (type.indexOf('json') != -1) {
                option.success(JSON.parse(xhr.responseText));
            }
            // 是否为xml
            else if (type.indexOf('xml') != -1) {
                option.success(xhr.responseXML);
            }
            // 普通字符串
            else {
                option.success(xhr.responseText);
            }
        }
    }
    xhr.send(option.data);
}
```

> 注意，上面代码设置了在不同的返回数据类型下，用了判断语句返回需要的格式。`getResponseHeader('Content-Type')`可以得到请求头的类型。`indexOf`函数可以判断在数据或字符串中是否有对应的子串。

**html文件**：

```js
// 获取json
document.querySelector('.json').onclick = function(){
    ajax({ // 顺序可以不一样，但是键名一定要按照规范写
        type:'get',
        url:'../00.backData/backJSON.php',
        success:function(data){
            console.log(data);
        }
    })
}

// 获取 xml
document.querySelector('.xml').onclick = function(){
    ajax({
        type:'post',
        url:'../00.backData/backXML.php',
        success:function(data){
            console.log(data);
        }
    })
}
```

#### 4. 注册页面点击案例

**要求**：

```markdown
需求1 
	失去焦点
		开启遮罩层 -- cover
		--ajax验证用户名
			调用验证用户名接口
		请求回来之后
			关闭遮罩层、修改文本框之后的提示、延迟一会之后消失
需求2
	按钮根据是否可以注册 变绿
需求3
	点击注册按钮 弹出遮罩层
	请求回来之后
		关闭遮罩层、信息设置给提示tips
需求4
	注册按钮 不能一直点
	当注册按钮 有disable这个类 就不能点
需求5
	注册成功之后  禁用按钮的点击
```

**html的JS部分**：

```js
// 需求1
$('.inputName').blur(function () {
    $('.cover').show();
    // 发送请求
    ajax({
        type: 'get',
        url: '_api/01.check.php',
        data: 'name=' + $('.inputName').val(),
        success: function (data) {
            console.log(data);
            $('.cover').hide();
            // delay 让后面的动画 延迟一会调用
            $('.tips').html(data.message).fadeIn(1000).delay(2000).fadeOut();
            // 如果可以注册 删除类名即可
            if (data.status == 'can') {
                $('.sub').removeClass('disabled');
            }
            if (data.status == 'cannot') {
                $('.sub').addClass('disabled');
            }
        }
    })
})

// 需求3
$('.sub').click(function(){
    if($(this).hasClass('disabled')==true){
        alert('哥们,别点了');
        return;
    }
    $('.cover').show();
    ajax({
        url:'_api/register.php',
        type:'post',
        data:'name='+$('.inputName').val(),
        success:function(data){
            $('.cover').hide();
            $('.tips').html(data).fadeIn(1000).delay(1000).fadeOut(1000);
            // 添加禁用的类名即可
            $('.sub').addClass('disabled');
        }
    })
})
```

> 注意：其它部分就是上节的代码；另外，hasClass方法可以判断某个DOM元素是否有这个类名。

#### 5. JQuery中的AJAX

官方手册：https://jquery.cuishifeng.cn/

**get请求**：

```js
// 支持传入js对象
$.get('../00.backData/01.backSendData.php',{name:'黑猫警长',skill:'抓老鼠'}, function (data) {
    alert(data);
})
```

**post请求**：

```js
// 支持传入js对象
$.post('../00.backData/01.backSendData.php',{name:'飞天小女警',skill:'自由飞翔'}, function (data) {
    alert(data);
})
```

**综合写法**：

**格式**

```js
jQuery.ajax(url,[settings]) // 参数是对象类型，url必写
```

```js
// 可以自己选择 get 还是post
$.ajax({
    url:'../00.backData/backXML.php',
    // type:'post',
    // date:'memeda',
    success:function(data){
        console.log(data);
    }
})
```

注意：

- `type` 如果不设置 默认的请求方法是`get`
- `success`在请求成功才会触发。如果出现 服务器告诉浏览器返回的类型 跟 `jQuery`内部实际转换的类型不匹配 会无法触发。
- `error事件`是请求失败时显示信息。
- `complete事件` 是无论是否失败，请求完成会触发。

**发送验证码案例**：

**实现要求**

1、用户名 name 失去焦点 验证数据 

2、手机号 mobile 失去焦点 验证数据 

3、验证码倒计时功能以及禁用

```js
$('.name').blur(function () { // 失去焦点 验证数据
    // 为了在代码中 使用this 不出现问题
    var $this = $(this);
    // 发送ajax 请求
    $.ajax({
        url: '_api/checkName.php',
        data: {
            name: $this.val()
        },
        success: function (data) {
            $('.tips').find('p').html(data).fadeIn(1000).delay(1000).fadeOut(1000);
        }
    })
})
```

```js
$('.mobile').blur(function () { // 失去焦点 验证数据 
    //
    $.ajax({
        url: '_api/checkMobile.php',
        type: 'post',
        data: { // 这是对象
            mobile: $('.mobile').val()
        },
        success: function (data) {
            $('.tips p').html(data).fadeIn(1000).delay(1000).fadeOut(1000);
        }
    })
})
```

```js
$('.verify').click(function () { // 验证码倒计时功能以及禁用
    // 判断拥有类名时 不能继续点击
    if ($(this).hasClass('disabled')) {
        return;
    }
    $(this).addClass('disabled');
    // 定义倒计时的时间
    var totalTime = 4;
    // 直接修改内容即可
    $(this).val('还有' + totalTime + 'S');
    // 定时器 实现倒计时功能
    var interId = setInterval(function () {
        totalTime--;
        if (totalTime == 0) {
            // 清除定时器
            clearInterval(interId);
            $('.verify').removeClass('disabled');
            $('.verify').val('获取验证码');
            // 阻断后续代码执行
            return;
        }
        $('.verify').val('还有' + totalTime + 'S');
    }, 1000)
    // 获取验证码
    $.ajax({
        url: "_api/code.php",
        data: {
            mobile: $('.mobile').val()
        },
        success: function (data) {
            console.log(data);
            $('.code').val(data);
        }
    })
})
```

### 五、模板引擎

> 如果需要修改的DOM对象太多，重复性的块元素又很多，那么可以定义一个模板引擎，只需要在大的布局下挖掉关键的信息，然后再往里面填信息就可以节省大量的代码。

项目地址：https://aui.github.io/art-template/

#### 1. 基本用法

**html中**：

```html
//定义模板
<script src="lib/template-web.js"></script>
<script type='text/html' id='template'> // id必须要写
    <ul>
        <li>名字{{name}}</li>
        <li>技能{{skill}}</li>
        <li>爱好{{habbit}}</li>
    </ul>
</script>
```

> 注意：`type='text/html'`是必须的，若不写或者写`text/javascript`会被解析为 `js`代码。

```html
<script>
    var data = {
        name:'zjgsujzx',
        skill:'写代码',
        habbit:'看动漫'
    };
    // 填坑
    // 参数1 模板的id
    // 参数2 填充的数据
    var result = template('template',data); // 需要引入template-web.js
    console.log(result);
    document.body.innerHTML = result;
</script>
```

> 要点：要写`id`，对应`template`方法的第一个参数名字；第二个参数是写传入的数据对象`data`，要按照API文档格式写。返回值是`html`结构的`DOM`元素。

#### 2. 落网案例

**要求**：

- 类似一个音乐网站，点击按钮出现一首或多首歌曲。

```html
<!--  导入模板引擎  -->
<script src='./js/template-web.js'></script>
<!-- 定义模板  -->
<script type='text/html' id='template'> // id名记得写
    <div class="item">
        <a href="#" class="cover"><img src="{{path}}" alt=""></a>
        <div class="bottom">
            <a href="#">{{name}}</a>
            <div class="rightBox">
                <span class="icon-heart">{{star}}</span>
                <span class="icon-comment">{{message}}</span>
            </div>
        </div>
    </div>
</script>
```

```html
<script>
    // 获取数据
    $(function(){ // 入口函数
        $('#getMore').click(function(){ // 点击事件
            $.ajax({ // JQ定义号的函数封装，默认为get
                url:'_api/luowang.php',
                data:{
                    index:3 // 是按API要求写的
                },
                success:function(data){
                    var result =   template('template',data.item);
                    $('.container').append(result); // 添加DOM对象元素
                }
            })
        })

        // 获取多条
        $('#getSome').click(function(){
            $.ajax({
                url:'_api/luowang_getSome.php',
                data:{
                    num:Math.floor((16*Math.random())) // 随机数返回调用数量
                },
                success:function(data){
                    // 循环 填坑
                    for(var i =0;i<data.items.length;i++){
                        // 填坑 使用
                        $('.container').append(template('template',data.items[i]));
                    }
                }
            })
        })
    })
</script>
```

> 补充一个API网站，可用来练习：https://api.asilu.com/

**补充内容1**：

如果在php里没有`header`来指定返回的数据格式，前端可以人为在JS里`dataType`加上。如：

```js
$('.json').click(function () {
    // 开启
    $.ajax({
        url: '../00.backData/backJSON.php',
        success: function (data) {
        },
        // 人为的指定 返回的数据格式
        dataType: 'json'
    })
})
```

**补充内容2**：

如果要给多个DOM元素绑定<u>一样的AJAX事件</u>，可以通过`ajaxStart`来实现。同理`ajaxComplete`也可以实现。

```js
$('button').ajaxStart(function () {
    $('.cover').hide();
});
```

#### 3. 模板引擎原理

首先需要了解正则表达式的部分内容。

```js
var str = '我是一匹来自{{place}}的西兰花,我生长在无垠的{{hometown}}中';
// 定义正则
// {{开头  字母\w 最起码1个+  }}结尾
// 提供了一个 再次检索的功能 语法是 想要再次检索的内容 用 小括号包起来
var reg = /{{(\w+)}}/;
```

> 如果使用`console.log(reg.test(str))`，结果返回`true`。说明查找到可以替换的值。

用`console.log(reg.exec(str))`，会返回一个数组：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/05/78683c1ada80bf474e697f505cb59693.png" alt="78683c1ada80bf474e697f505cb59693.png" border="0" />

接下来就可以实现自己的模板引擎了。

```js
// 抽取 公共的部分
// 不确定的 作为参数
// 结果 返回给用户
function my_template(id,data){
    // 字符串
    var str = document.querySelector('#'+id).innerHTML;
    // 定义正则
    var reg = /{{(\w+)}}/;
    // 循环替换 直到 为null 结束
    var result = reg.exec(str);
    while(result){
        str = str.replace(result[0],data[result[1]]);
        result = reg.exec(str);
    }
    // 获取结果
    return str;
}
```

> 要点是调用对象里的属性，可以通过`对象名[属性名]`的形式调用。

#### 4. 模板引擎更多功能使用

**1、{{if}}判断**

格式为：

```
{{if 属性名=='属性值1'}}
{{else if 属性名=='属性值2'}}
{{/if}}
```

```html
<script id='ifTemplate' type="text/html">
    <ul>
        {{if male=='女'}}
        <li>欢迎您 {{name}} 女士
            <ol>
                <li>这是最新款的包包</li>
                <li>这是最新款的口红</li>
                <li>没想到,你竟然是{{skill}}</li>
            </ol>
        </li>
        {{else if male=='男'}}
        <li>欢迎您 {{name}} 先生
            <ol>
                <li>这是最新款的拖拉机</li>
                <li>讨厌,才来找人家</li>
                <li>没想到,你竟然稍长{{skill}}</li>
            </ol>
        </li>
        {{/if}}
    </ul>
</script>
<script>
    var person1 = {
        male: '女',
        name: '郑爽',
        skill: '身材好'
    };
    var person2 = {
        male: '男',
        name: '张翰',
        skill: '这篇鱼塘我承包了'
    };
    console.log(template('ifTemplate', person1));
    console.log(template('ifTemplate', person2));
</script>
```

**2、标签原文输出{{@value}}**

格式为：

```
{{@value}}
```

```html
<script id='norTemplate' type="text/html">
    <ul>
        <li>{{name}}</li>
        <li>{{skill}}</li>
        <li>{{@info}}</li>
    </ul>
</script>
<script>
    var person = {
        name:'犬夜叉',
        skill:'变犬',
        info:'<a href="https://baike.baidu.com/item/%E7%8A%AC%E5%A4%9C%E5%8F%89/26878?fr=aladdin">犬夜叉</a>'
    }
    document.body.innerHTML = template('norTemplate',person);
</script>
```

**3、循环语句**

格式：

```
{{each 属性名}}
{{/each}}
```

```html
<script id='eachTemplate' type="text/html">
    <ul>
        <li>{{name}}</li>
        <li>兄弟们
            {{each brother}}
        <li>{{$value}}</li>
        {{/each}}
        </li>
        <li>家人们
            <ol>
                {{each family}} // 注意这是属性名
                <li>{{$value.name}}---{{$value.skill}}</li> // 调用类属性的值要用 $value.属性名，其中$value是类名
                {{/each}}
            </ol>
        </li>
    </ul>
</script>
<script>
    var person = {
        name:'大娃',
        brother:[
            '二娃',
            '三娃'
        ],
        family:[
            {name:'爷爷',skill:'被抓'},
            {name:'小蝴蝶',skill:'撩--葫芦娃'}
        ]
    }
    console.log(template('eachTemplate',person));
</script>
```

#### 5. 瀑布流布局插件

masonry使用文档：https://masonry.desandro.com/

### 六、同源与跨域

#### 1. 同源

http://127.0.0.1/2017-8-17/09.waterFall_ajax/

http://127.0.0.1/2017-8-17/09.waterFall_ajax/api/waterFall.php

> 协议名:**http**一样、**地址**一样、**端口号**（默认是80端口）一样
>
> 上述三个条件一样称之为**同源**

#### 2. 跨域

**不同源**：协议、地址、端口号，有一个不一样，称之为不同源

**跨域**：不同源的网站之前，互相发送请求称为跨域

**解决方法**：`datatype`设置为`jsonp`

#### 3. JSONP的原理

```html
<!-- dom元素的 src属性 是支持 跨域获取资源的 -->
<img src="https://ss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo/bd_logo1_31bdc765.png" alt="">

<!--  还有 那些元素 有src属性 -->
<script src='http://192.168.70.78/2017-8-17/12.JSONP/backData.js'></script>
```

> `JSONP` 就是利用了 `src`属性 支持跨域获取资源

```html
<!-- JSONP的真实用法 -->
<script>
    function doSomething(data){
        console.log(data);
    }
</script>
<script  src="http://192.168.70.78/2017-8-17/12.JSONP/backData.php?callback=doSomething">
    // 等同于doSomething({"name":"jack","food":"西兰花"})
</script>
```

```php
<?php 
  // echo 'console.log("数据给你,拿去")';
  // doSomething
  $methodName = $_GET['callback'];

  // 把数据 拼接到 函数名的后面
  echo $methodName.'({"name":"jack","food":"西兰花"})';
?>
```







































