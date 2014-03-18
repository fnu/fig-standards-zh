Coding Style Guide
==================

代码风格指南
==================

This guide extends and expands on [PSR-1], the basic coding standard.

本指南在基本编码标准 [PSR-1] 之上进行延伸和扩展。

The intent of this guide is to reduce cognitive friction when scanning code
from different authors. It does so by enumerating a shared set of rules and
expectations about how to format PHP code.

本指南的意图是提升我们阅读不同开发者代码的效率。
下面列举了一些有关如何格式化PHP代码的常用规范。

The style rules herein are derived from commonalities among the various member
projects. When various authors collaborate across multiple projects, it helps
to have one set of guidelines to be used among all those projects. Thus, the
benefit of this guide is not in the rules themselves, but in the sharing of
those rules.

这组代码风格规范由各个项目之间的共性组成。
当开发者们在多个项目中合作时，这有助于有一套规范在所有这些项目中使用。
因此，本指南的益处不在于这些规则本身，而在于在所有项目中共用这些规则。

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119].

[RFC 2119] 中的必须(MUST)，不能(MUST NOT)，
建议(SHOULD)，不建议(SHOULD NOT)，可以/可能(MAY)等关键词
将在本节用来做一些解释性的描述。

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/tangrucheng/fig-standards-zh/blob/master/PSR-0.md
[PSR-1]: https://github.com/tangrucheng/fig-standards-zh/blob/master/PSR-1-basic-coding-standard.md


1. Overview
-----------

1. 概述
-----------

- Code MUST follow a "coding style guide" PSR [[PSR-1]].

- 代码必须遵守 PSR [[PSR-1]]。

- Code MUST use 4 spaces for indenting, not tabs.

- 代码必须使用4个空格来缩进，而不是用制表符。

- There MUST NOT be a hard limit on line length; the soft limit MUST be 120
  characters; lines SHOULD be 80 characters or less.

- 一行代码不建议有硬限制；软限制必须为120字符，建议每行代码80个字符或更少。

- There MUST be one blank line after the `namespace` declaration, and there
  MUST be one blank line after the block of `use` declarations.

- 在命名空间 `namespace` 的声明下面必须有一行空行，并且在导入 `use` 的声明下面也必须有一行空行。

- Opening braces for classes MUST go on the next line, and closing braces MUST
  go on the next line after the body.

- 类的左花括号必须放到其声明下面自成一行，右花括号则必须放到类主体下面自成一行。

- Opening braces for methods MUST go on the next line, and closing braces MUST
  go on the next line after the body.

- 方法的左花括号必须放到其声明下面自成一行，右花括号则必须放到方法主体下面自成一行。

- Visibility MUST be declared on all properties and methods; `abstract` and
  `final` MUST be declared before the visibility; `static` MUST be declared
  after the visibility.

- 所有的属性和方法必须有可见性声明；
  `abstract` 和 `final` 声明必须在可见性声明之前；
  `static` 声明必须在可见性声明之后。

- Control structure keywords MUST have one space after them; method and
  function calls MUST NOT.

- 在控制结构关键字的后面必须有一个空格；
  方法和函数的声明后面不可有空格。

- Opening braces for control structures MUST go on the same line, and closing
  braces MUST go on the next line after the body.

- 控制结构的左花括号必须跟其放在同一行，右花括号必须放在该控制结构代码主体的下一行。

- Opening parentheses for control structures MUST NOT have a space after them,
  and closing parentheses for control structures MUST NOT have a space before.

- 控制结构的左圆括号之后不可有空格，右圆括号之前也不可有空格。

### 1.1. Example

### 1.1. 示例

This example encompasses some of the rules below as a quick overview:

下面示例中简单展示了上文中提到的一些规则：

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // method body
    }
}
```

2. General
----------

2. 常规代码风格规范
----------

### 2.1 Basic Coding Standard

### 2.1 基础代码规范

Code MUST follow all rules outlined in [PSR-1].

代码必须遵守 [PSR-1] 中的所有规则。

### 2.2 Files

### 2.2 文件

All PHP files MUST use the Unix LF (linefeed) line ending.

所有的PHP文件必须使用 Unix LF (换行符) 作为行结束符。

All PHP files MUST end with a single blank line.

所有PHP文件必须以一个空行结束

The closing `?>` tag MUST be omitted from files containing only PHP.

纯PHP代码文件的关闭标签 `?>` 必须省略。

### 2.3. Lines

### 2.3. 行

There MUST NOT be a hard limit on line length.

行长度不可以有硬限制。

The soft limit on line length MUST be 120 characters; automated style checkers
MUST warn but MUST NOT error at the soft limit.

行长度的软限制必须是120字符；对于软限制，代码风格检查器必须警告但不报错。

Lines SHOULD NOT be longer than 80 characters; lines longer than that SHOULD
be split into multiple subsequent lines of no more than 80 characters each.

一行代码的长度不建议超过80个字符；较长的行建议拆分成多个不超过80个字符的子行。

There MUST NOT be trailing whitespace at the end of non-blank lines.

在非空行后面不可有空格。

Blank lines MAY be added to improve readability and to indicate related
blocks of code.

空行可以用来增强可读性和区分相关代码块。

There MUST NOT be more than one statement per line.

一行不可多于一个语句。

### 2.4. Indenting

### 2.4. 缩进

Code MUST use an indent of 4 spaces, and MUST NOT use tabs for indenting.

代码必须使用4个空格，且不可使用制表符来作为缩进。

> N.b.: Using only spaces, and not mixing spaces with tabs, helps to avoid
> problems with diffs, patches, history, and annotations. The use of spaces
> also makes it easy to insert fine-grained sub-indentation for inter-line 
> alignment.

> 注意：代码中只使用空格，且不和制表符混合使用，
> 将会对避免代码差异，补丁，历史和注解中的一些问题有帮助。
> 空格的使用还可以使通过调整细微的缩进来改进行间对齐变得更加的简单。

### 2.5. Keywords and True/False/Null

### 2.5. 关键字 和 True/False/Null

PHP [keywords] MUST be in lower case.

PHP [关键字] 必须使用小写字母。

The PHP constants `true`, `false`, and `null` MUST be in lower case.

PHP常量  `true`，`false`和 `null` 必须使用小写字母。

[关键字]: http://php.net/manual/en/reserved.keywords.php



3. Namespace and Use Declarations
---------------------------------

3. Namespace 和 Use 声明
---------------------------------

When present, there MUST be one blank line after the `namespace` declaration.

命名空间 `namespace` 的声明后面必须有一空行。

When present, all `use` declarations MUST go after the `namespace`
declaration.

所有的 `use` 声明必须放在命名空间 `namespace` 声明的下面。

There MUST be one `use` keyword per declaration.

每个声明中，必须有一个导入 `use` 关键字。

There MUST be one blank line after the `use` block.

在 `use` 声明代码块后面必须有一空行。

For example:

示例：

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... additional PHP code ...

```


4. Classes, Properties, and Methods
-----------------------------------

4. 类，属性，和方法
-----------------------------------

The term "class" refers to all classes, interfaces, and traits.

术语“类”指类（class），接口（interface），和 特性（traits）。

### 4.1. Extends and Implements

### 4.1. Extends 和 Implements

The `extends` and `implements` keywords MUST be declared on the same line as
the class name.

一个类的 `extends` 和 `implements` 关键字必须和类名在同行。

The opening brace for the class MUST go on its own line; the closing brace
for the class MUST go on the next line after the body.

类的左花括号必须放在下面自成一行；
右花括号必须放在类主体的后面自成一行。

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

Lists of `implements` MAY be split across multiple lines, where each
subsequent line is indented once. When doing so, the first item in the list
MUST be on the next line, and there MUST be only one interface per line.

`implements` 列表可以被拆分为多个缩进了一次的子行。
如果要拆成多个子行，列表的第一项必须要放在下一行，
并且每行必须只有一个接口。

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```

### 4.2. Properties

### 4.2. 属性

Visibility MUST be declared on all properties.

所有属性都必须声明其可见性。

The `var` keyword MUST NOT be used to declare a property.

`var` 关键字不可用来声明一个属性。

There MUST NOT be more than one property declared per statement.

每个声明不得超过一个属性。

Property names SHOULD NOT be prefixed with a single underscore to indicate
protected or private visibility.

属性名不推荐用单个下划线作为前缀来表明其保护或私有的可见性。

A property declaration looks like the following.

一个属性声明看起来应该像下面这样。

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

### 4.3. Methods

### 4.3. 方法

Visibility MUST be declared on all methods.

所有的方法都必须声明其可见性。

Method names SHOULD NOT be prefixed with a single underscore to indicate
protected or private visibility.

方法名不推荐用单个下划线作为前缀来表明其保护或私有的可见性。

Method names MUST NOT be declared with a space after the method name. The
opening brace MUST go on its own line, and the closing brace MUST go on the
next line following the body. There MUST NOT be a space after the opening
parenthesis, and there MUST NOT be a space before the closing parenthesis.

方法名在其声明后面不可有空格跟随。
其左花括号必须放在下面自成一行，且右花括号必须放在方法主体的下面自成一行。
左括号后面不可有空格，且右括号前面也不可有空格。

A method declaration looks like the following. Note the placement of
parentheses, commas, spaces, and braces:

一个方法声明看来应该像下面这样。 注意括号，逗号，空格和花括号的位置：

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```    

### 4.4. Method Arguments

### 4.4. 方法的参数

In the argument list, there MUST NOT be a space before each comma, and there
MUST be one space after each comma.

在参数列表中，逗号之前不可有空格，而逗号之后则必须要有一个空格。

Method arguments with default values MUST go at the end of the argument
list.

方法中有默认值的参数必须放在参数列表的最后面。

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

Argument lists MAY be split across multiple lines, where each subsequent line
is indented once. When doing so, the first item in the list MUST be on the
next line, and there MUST be only one argument per line.

参数列表可以被拆分为多个缩进了一次的子行。
如果要拆分成多个子行，
参数列表的第一项必须放在下一行，
并且每行必须只有一个参数。

When the argument list is split across multiple lines, the closing parenthesis
and opening brace MUST be placed together on their own line with one space
between them.

当参数列表被拆分成多个子行，右括号和左花括号之间必须有一个空格并且自成一行。

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```

### 4.5. `abstract`, `final`, and `static`

### 4.5. `abstract`, `final`, 和 `static`

When present, the `abstract` and `final` declarations MUST precede the
visibility declaration.

当用到 `abstract` 和 `final` 来声明时，它们必须放在可见性声明的前面。

When present, the `static` declaration MUST come after the visibility
declaration.

而当用到静态 `static` 来声明时，则必须放在可见性声明的后面。

```php
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // method body
    }
}
```

### 4.6. Method and Function Calls

### 4.6. 条用方法和函数

When making a method or function call, there MUST NOT be a space between the
method or function name and the opening parenthesis, there MUST NOT be a space
after the opening parenthesis, and there MUST NOT be a space before the
closing parenthesis. In the argument list, there MUST NOT be a space before
each comma, and there MUST be one space after each comma.

调用一个方法或函数时，在方法名或者函数名和左括号之间不可有空格，
左括号之后不可有空格，右括号之前也不可有空格。
参数列表中，逗号之前不可有空格，逗号之后则必须有一个空格。

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

Argument lists MAY be split across multiple lines, where each subsequent line
is indented once. When doing so, the first item in the list MUST be on the
next line, and there MUST be only one argument per line.

参数列表可以被拆分成多个缩进了一次的子行。
如果拆分成子行，列表中的第一项必须放在下一行，
并且每一行必须只能有一个参数。

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```

5. Control Structures

5. 控制结构
---------------------

The general style rules for control structures are as follows:

下面是对于控制结构代码风格的概括：

- There MUST be one space after the control structure keyword
- 控制结构的关键词之后必须有一个空格。
- There MUST NOT be a space after the opening parenthesis
- 控制结构的左括号之后不可有空格。
- There MUST NOT be a space before the closing parenthesis
- 控制结构的右括号之前不可有空格。
- There MUST be one space between the closing parenthesis and the opening
  brace
- 控制结构的右括号和左花括号之间必须有一个空格。
- The structure body MUST be indented once
- 控制结构的代码主体必须进行一次缩进。
- The closing brace MUST be on the next line after the body
- 控制结构的右花括号必须主体的下一行。

The body of each structure MUST be enclosed by braces. This standardizes how
the structures look, and reduces the likelihood of introducing errors as new
lines get added to the body.

每个控制结构的代码主体必须被括在花括号里。
这样可是使代码看上去更加标准化，
并且加入新代码的时候还可以因此而减少引入错误的可能性。


### 5.1. `if`, `elseif`, `else`

An `if` structure looks like the following. Note the placement of parentheses,
spaces, and braces; and that `else` and `elseif` are on the same line as the
closing brace from the earlier body.

下面是一个 `if` 条件控制结构的示例，注意其中括号，空格和花括号的位置。
同时注意 `else` 和 `elseif` 要和前一个条件控制结构的右花括号在同一行。

```php
<?php
if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```

The keyword `elseif` SHOULD be used instead of `else if` so that all control
keywords look like single words.

推荐用 `elseif` 来替代 `else if` ，以保持所有的条件控制关键字看起来像是一个单词。


### 5.2. `switch`, `case`

A `switch` structure looks like the following. Note the placement of
parentheses, spaces, and braces. The `case` statement MUST be indented once
from `switch`, and the `break` keyword (or other terminating keyword) MUST be
indented at the same level as the `case` body. There MUST be a comment such as
`// no break` when fall-through is intentional in a non-empty `case` body.

下面是一个 `switch` 条件控制结构的示例，注意其中括号，空格和花括号的位置。
`case` 语句必须要缩进一级，
而 `break` 关键字（或其他中止关键字）必须和 `case` 结构的代码主体在同一个缩进层级。
如果一个有主体代码的 `case` 结构故意的继续向下执行，
则必须要有一个类似于 `// no break` 的注释。

```php
<?php
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```


### 5.3. `while`, `do while`

A `while` statement looks like the following. Note the placement of
parentheses, spaces, and braces.

下面是一个 `while` 循环控制结构的示例，注意其中括号，空格和花括号的位置。

```php
<?php
while ($expr) {
    // structure body
}
```

Similarly, a `do while` statement looks like the following. Note the placement
of parentheses, spaces, and braces.

下面是一个 `do while` 循环控制结构的示例，注意其中括号，空格和花括号的位置。

```php
<?php
do {
    // structure body;
} while ($expr);
```

### 5.4. `for`

A `for` statement looks like the following. Note the placement of parentheses,
spaces, and braces.

下面是一个 `for` 循环控制结构的示例，注意其中括号，空格和花括号的位置。

```php
<?php
for ($i = 0; $i < 10; $i++) {
    // for body
}
```

### 5.5. `foreach`
    
A `foreach` statement looks like the following. Note the placement of
parentheses, spaces, and braces.

下面是一个 `foreach` 循环控制结构的示例，注意其中括号，空格和花括号的位置。

```php
<?php
foreach ($iterable as $key => $value) {
    // foreach body
}
```

### 5.6. `try`, `catch`

A `try catch` block looks like the following. Note the placement of
parentheses, spaces, and braces.

下面是一个 `try catch` 异常处理控制结构的示例，注意其中括号，空格和花括号的位置。

```php
<?php
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}
```

6. Closures
-----------

6. 闭包
-----------

Closures MUST be declared with a space after the `function` keyword, and a
space before and after the `use` keyword.

声明闭包时所用的 `function` 关键字之后必须要有一个空格，
而 `use` 关键字的前后都要有一个空格。

The opening brace MUST go on the same line, and the closing brace MUST go on
the next line following the body.

闭包的左花括号必须跟其在同一行，而右花括号必须在闭包主体的下一行。

There MUST NOT be a space after the opening parenthesis of the argument list
or variable list, and there MUST NOT be a space before the closing parenthesis
of the argument list or variable list.

闭包的参数列表和变量列表的左括号后面不可有空格，右括号的前面也不可有空格。

In the argument list and variable list, there MUST NOT be a space before each
comma, and there MUST be one space after each comma.

闭包的参数列表和变量列表中逗号前面不可有空格，而逗号后面则必须有空格。

Closure arguments with default values MUST go at the end of the argument
list.

闭包的参数列表中带默认值的参数必须放在参数列表的结尾部分。

A closure declaration looks like the following. Note the placement of
parentheses, commas, spaces, and braces:

下面是一个闭包的示例。注意括号，空格和花括号的位置。

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};
```

Argument lists and variable lists MAY be split across multiple lines, where
each subsequent line is indented once. When doing so, the first item in the
list MUST be on the next line, and there MUST be only one argument or variable
per line.

参数列表和变量列表可以被拆分成多个缩进了一级的子行。
如果要拆分成多个子行，列表中的第一项必须放在下一行，
并且每一行必须只放一个参数或变量。

When the ending list (whether or arguments or variables) is split across
multiple lines, the closing parenthesis and opening brace MUST be placed
together on their own line with one space between them.

当列表（不管是参数还是变量）最终被拆分成多个子行，
右括号和左花括号之间必须要有一个空格并且自成一行。

The following are examples of closures with and without argument lists and
variable lists split across multiple lines.

下面是一个参数列表和变量列表被拆分成多个子行的示例。

```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};
```

Note that the formatting rules also apply when the closure is used directly
in a function or method call as an argument.

把闭包作为一个参数在函数或者方法中调用时，依然要遵守上述规则。

```php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
```


7. Conclusion
--------------

7. 总结
--------------

There are many elements of style and practice intentionally omitted by this
guide. These include but are not limited to:

本指南有意的省略了许多元素的代码风格。主要包括：

- Declaration of global variables and global constants

- 全局变量和全局常量的声明

- Declaration of functions

- 函数声明

- Operators and assignment

- 操作符合赋值

- Inter-line alignment

- 行间对齐

- Comments and documentation blocks

- 注释和文档块

- Class name prefixes and suffixes

- 类名的前缀和后缀

- Best practices

- 最佳实践

Future recommendations MAY revise and extend this guide to address those or
other elements of style and practice.

以后的代码规范中可能会修正或扩展本指南中规定的代码风格。

Appendix A. Survey
------------------

附录A 调查
------------------

In writing this style guide, the group took a survey of member projects to
determine common practices.  The survey is retained herein for posterity.

为了写这个风格指南，我们调查了各个项目以最终确定通用的代码风格。
并把这次调查在这里公布出来。

### A.1. Survey Data

### A.1. 调查数据

    url,http://www.horde.org/apps/horde/docs/CODING_STANDARDS,http://pear.php.net/manual/en/standards.php,http://solarphp.com/manual/appendix-standards.style,http://framework.zend.com/manual/en/coding-standard.html,http://symfony.com/doc/2.0/contributing/code/standards.html,http://www.ppi.io/docs/coding-standards.html,https://github.com/ezsystems/ezp-next/wiki/codingstandards,http://book.cakephp.org/2.0/en/contributing/cakephp-coding-conventions.html,https://github.com/UnionOfRAD/lithium/wiki/Spec%3A-Coding,http://drupal.org/coding-standards,http://code.google.com/p/sabredav/,http://area51.phpbb.com/docs/31x/coding-guidelines.html,https://docs.google.com/a/zikula.org/document/edit?authkey=CPCU0Us&hgd=1&id=1fcqb93Sn-hR9c0mkN6m_tyWnmEvoswKBtSc0tKkZmJA,http://www.chisimba.com,n/a,https://github.com/Respect/project-info/blob/master/coding-standards-sample.php,n/a,Object Calisthenics for PHP,http://doc.nette.org/en/coding-standard,http://flow3.typo3.org,https://github.com/propelorm/Propel2/wiki/Coding-Standards,http://developer.joomla.org/coding-standards.html
    voting,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,no,no,no,?,yes,no,yes
    indent_type,4,4,4,4,4,tab,4,tab,tab,2,4,tab,4,4,4,4,4,4,tab,tab,4,tab
    line_length_limit_soft,75,75,75,75,no,85,120,120,80,80,80,no,100,80,80,?,?,120,80,120,no,150
    line_length_limit_hard,85,85,85,85,no,no,no,no,100,?,no,no,no,100,100,?,120,120,no,no,no,no
    class_names,studly,studly,studly,studly,studly,studly,studly,studly,studly,studly,studly,lower_under,studly,lower,studly,studly,studly,studly,?,studly,studly,studly
    class_brace_line,next,next,next,next,next,same,next,same,same,same,same,next,next,next,next,next,next,next,next,same,next,next
    constant_names,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper
    true_false_null,lower,lower,lower,lower,lower,lower,lower,lower,lower,upper,lower,lower,lower,upper,lower,lower,lower,lower,lower,upper,lower,lower
    method_names,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel,lower_under,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel
    method_brace_line,next,next,next,next,next,same,next,same,same,same,same,next,next,same,next,next,next,next,next,same,next,next
    control_brace_line,same,same,same,same,same,same,next,same,same,same,same,next,same,same,next,same,same,same,same,same,same,next
    control_space_after,yes,yes,yes,yes,yes,no,yes,yes,yes,yes,no,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes
    always_use_control_braces,yes,yes,yes,yes,yes,yes,no,yes,yes,yes,no,yes,yes,yes,yes,no,yes,yes,yes,yes,yes,yes
    else_elseif_line,same,same,same,same,same,same,next,same,same,next,same,next,same,next,next,same,same,same,same,same,same,next
    case_break_indent_from_switch,0/1,0/1,0/1,1/2,1/2,1/2,1/2,1/1,1/1,1/2,1/2,1/1,1/2,1/2,1/2,1/2,1/2,1/2,0/1,1/1,1/2,1/2
    function_space_after,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no
    closing_php_tag_required,no,no,no,no,no,no,no,no,yes,no,no,no,no,yes,no,no,no,no,no,yes,no,no
    line_endings,LF,LF,LF,LF,LF,LF,LF,LF,?,LF,?,LF,LF,LF,LF,?,,LF,?,LF,LF,LF
    static_or_visibility_first,static,?,static,either,either,either,visibility,visibility,visibility,either,static,either,?,visibility,?,?,either,either,visibility,visibility,static,?
    control_space_parens,no,no,no,no,no,no,yes,no,no,no,no,no,no,yes,?,no,no,no,no,no,no,no
    blank_line_after_php,no,no,no,no,yes,no,no,no,no,yes,yes,no,no,yes,?,yes,yes,no,yes,no,yes,no
    class_method_control_brace,next/next/same,next/next/same,next/next/same,next/next/same,next/next/same,same/same/same,next/next/next,same/same/same,same/same/same,same/same/same,same/same/same,next/next/next,next/next/same,next/same/same,next/next/next,next/next/same,next/next/same,next/next/same,next/next/same,same/same/same,next/next/same,next/next/next

### A.2. Survey Legend

### A.2. 调查说明

`indent_type`:
The type of indenting. `tab` = "Use a tab", `2` or `4` = "number of spaces"

缩进类型。 `tab` = “使用制表符”，`2` or `4` = “空格数量”

`line_length_limit_soft`:
The "soft" line length limit, in characters. `?` = not discernible or no response, `no` means no limit.

行长度的“软”限制，用字符。 `?` = 不表示或者数字，`no` 意为不限制。

`line_length_limit_hard`:
The "hard" line length limit, in characters. `?` = not discernible or no response, `no` means no limit.

行长度的“硬”限制，用字符。 `?` = 不表示或者数字, `no` 意为不限制.

`class_names`:
How classes are named. `lower` = lowercase only, `lower_under` = lowercase with underscore separators, `studly` = StudlyCase.

类名如何命名 `lower` = 只是小写, `lower_under` = 小写加下划线, `studly` = 骆驼型.

`class_brace_line`:
Does the opening brace for a class go on the `same` line as the class keyword, or on the `next` line after it?

类的左花括号是放在同一行还是在下一行？

`constant_names`:
How are class constants named? `upper` = Uppercase with underscore separators.

类常量如何命名？`upper` = 大写加下划线分隔符。

`true_false_null`:
Are the `true`, `false`, and `null` keywords spelled as all `lower` case, or all `upper` case?

`true`, `false`, 和 `null` 关键字全 `lower` 或者 全 `upper`？

`method_names`:
How are methods named? `camel` = `camelCase`, `lower_under` = lowercase with underscore separators.

方法名如何命名？camel = 驼峰式, `lower_under` = 小写加下划线分隔符。

`method_brace_line`:
Does the opening brace for a method go on the `same` line as the method name, or on the `next` line?

方法的左花括号在同一行还是在下一行？

`control_brace_line`:
Does the opening brace for a control structure go on the `same` line, or on the `next` line?

控制结构的左花括号在同一行还是在下一行？

`control_space_after`:
Is there a space after the control structure keyword?

控制结构关键词后是否有空格？

`always_use_control_braces`:
Do control structures always use braces?

控制结构总是使用花括号？

`else_elseif_line`:
When using `else` or `elseif`, does it go on the `same` line as the previous closing brace, or does it go on the `next` line?

当使用else和elseif，是否放在同一行还是在下一行？

`case_break_indent_from_switch`:
How many times are `case` and `break` indented from an opening `switch` statement?

case和break分别从swith语句处缩进多少次？

`function_space_after`:
Do function calls have a space after the function name and before the opening parenthesis?

函数调用的函数名和左括号是否有空格？

`closing_php_tag_required`:
In files containing only PHP, is the closing `?>` tag required?

如过是纯PHP文件，关闭标签?>是否需要？

`line_endings`:
What type of line ending is used?

使用何种的行结束符？

`static_or_visibility_first`:
When declaring a method, does `static` come first, or does the visibility come first?

在定义方法的时候static和可见性谁在前面？

`control_space_parens`:
In a control structure expression, is there a space after the opening parenthesis and a space before the closing parenthesis? `yes` = `if ( $expr )`, `no` = `if ($expr)`.

在控制结构表达式中，左括号后面和右括号前面是否要有一个空格？yes = if ( $expr ), no = if ($expr).

`blank_line_after_php`:
Is there a blank line after the opening PHP tag?

PHP的开始标签后面是否需要一个空行？

`class_method_control_brace`:
A summary of what line the opening braces go on for classes, methods, and control structures.

左花括号在类，方法和控制结构中的位置。

### A.3. Survey Results

### A.3. 调查结果

    indent_type:
        tab: 7
        2: 1
        4: 14
    line_length_limit_soft:
        ?: 2
        no: 3
        75: 4
        80: 6
        85: 1
        100: 1
        120: 4
        150: 1
    line_length_limit_hard:
        ?: 2
        no: 11
        85: 4
        100: 3
        120: 2
    class_names:
        ?: 1
        lower: 1
        lower_under: 1
        studly: 19
    class_brace_line:
        next: 16
        same: 6
    constant_names:
        upper: 22
    true_false_null:
        lower: 19
        upper: 3
    method_names:
        camel: 21
        lower_under: 1
    method_brace_line:
        next: 15
        same: 7
    control_brace_line:
        next: 4
        same: 18
    control_space_after:
        no: 2
        yes: 20
    always_use_control_braces:
        no: 3
        yes: 19
    else_elseif_line:
        next: 6
        same: 16
    case_break_indent_from_switch:
        0/1: 4
        1/1: 4
        1/2: 14
    function_space_after:
        no: 22
    closing_php_tag_required:
        no: 19
        yes: 3
    line_endings:
        ?: 5
        LF: 17
    static_or_visibility_first:
        ?: 5
        either: 7
        static: 4
        visibility: 6
    control_space_parens:
        ?: 1
        no: 19
        yes: 2
    blank_line_after_php:
        ?: 1
        no: 13
        yes: 8
    class_method_control_brace:
        next/next/next: 4
        next/next/same: 11
        next/same/same: 1
        same/same/same: 6
