Basic Coding Standard
=====================

基本代码规范
=====================

This section of the standard comprises what should be considered the standard
coding elements that are required to ensure a high level of technical
interoperability between shared PHP code.

本节我们将会讨论一些基本的代码规范问题，
以此作为将来讨论更高级别的代码分享和技术互用的基础。

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119].

[RFC 2119] 中的必须(MUST)，不能(MUST NOT)，
建议(SHOULD)，不建议(SHOULD NOT)，可以/可能(MAY)等关键词
将在本节用来做一些解释性的描述。

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/tangrucheng/fig-standards-zh/blob/master/PSR-0.md
[PSR-4]: https://github.com/tangrucheng/fig-standards-zh/blob/master/PSR-4-autoloader.md


1. Overview
-----------

1. 概述
-----------

- Files MUST use only `<?php` and `<?=` tags.

- 文件必须只使用 `<?php` 和 `<?=` 这两种标签。

- Files MUST use only UTF-8 without BOM for PHP code.

- 文件中php代码的编码格式必须只使用无BOM头的UTF-8。

- Files SHOULD *either* declare symbols (classes, functions, constants, etc.)
  *or* cause side-effects (e.g. generate output, change .ini settings, etc.)
  but SHOULD NOT do both.

- 一个文件建议只用来做声明（类(class)，函数(function)，常量(constant)等）
或者只用来做一些引起副作用的操作（例如：输出信息，修改.ini配置等），
但不建议同时做这两件事。

- Namespaces and classes MUST follow an "autoloading" PSR: [[PSR-0], [PSR-4]].

- 命名空间(namespace)和类(class) 必须遵守PSR-0标准。

- Class names MUST be declared in `StudlyCaps`.

- 类名必须使用 `StudlyCaps` 写法 (译者注：StudlyCaps为大驼峰，后文将直接用StudlyCaps表示)。

- Class constants MUST be declared in all upper case with underscore separators.

- 类中的常量必须只由大写字母和下划线(_)组成。

- Method names MUST be declared in `camelCase`.

- 方法名必须使用 `cameCase` 写法(译者注：cameCase为小驼峰，后文将直接用camelCase表示)。


2. Files
--------

2. 文件
--------

### 2.1. PHP Tags

### 2.1. PHP标签

PHP code MUST use the long `<?php ?>` tags or the short-echo `<?= ?>` tags; it
MUST NOT use the other tag variations.

PHP代码必须只使用长标签(<?php ?>)或者短输出式标签(<?= ?>)；
而不可使用其他标签。

### 2.2. Character Encoding

### 2.2. 字符编码

PHP code MUST use only UTF-8 without BOM.

PHP代码的编码格式必须只使用无BOM头的UTF-8。

### 2.3. Side Effects

### 2.3. 副作用

A file SHOULD declare new symbols (classes, functions, constants,
etc.) and cause no other side effects, or it SHOULD execute logic with side
effects, but SHOULD NOT do both.

一个源文件建议只用来做声明（类(class)，函数(function)，常量(constant)等）
或者只用来做一些引起副作用的操作（例如：输出信息，修改.ini配置等），
但不建议同时做这两件事。

The phrase "side effects" means execution of logic not directly related to
declaring classes, functions, constants, etc., *merely from including the
file*.

短语副作用的意思是在包含文件时所执行的逻辑
与所声明的类(class)，函数(function)，常量(constant)等没有直接的关系。

"Side effects" include but are not limited to: generating output, explicit
use of `require` or `include`, connecting to external services, modifying ini
settings, emitting errors or exceptions, modifying global or static variables,
reading from or writing to a file, and so on.

副作用包含但不局限于：产生输出，显式地使用require或include，
连接外部服务，修改ini配置，触发错误或异常，修改全局或者静态变量，
读取或修改文件等等。

The following is an example of a file with both declarations and side effects;
i.e, an example of what to avoid:

下面是一个既包含声明又有副作用的示例文件；即应避免的例子：

```php
<?php
// side effect: change ini settings
ini_set('error_reporting', E_ALL);

// side effect: loads a file
include "file.php";

// side effect: generates output
echo "<html>\n";

// declaration
function foo()
{
    // function body
}
```

```php
<?php
// 副作用: 修改了ini配置
ini_set('error_reporting', E_ALL);

// side effect: 载入了文件
include "file.php";

// side effect: 产生了输出
echo "<html>\n";

// 声明
function foo()
{
    // 函数体
}
```

The following example is of a file that contains declarations without side
effects; i.e., an example of what to emulate:

下面是一个仅包含声明的示例文件；即应提倡的例子：

```php
<?php
// declaration
function foo()
{
    // function body
}

// conditional declaration is *not* a side effect
if (! function_exists('bar')) {
    function bar()
    {
        // function body
    }
}
```


```php
<?php
// 声明
function foo()
{
    // 函数体
}

// 条件式声明不算作是副作用
if (! function_exists('bar')) {
    function bar()
    {
        // 函数体
    }
}
```


3. Namespace and Class Names
----------------------------

3. 命名空间 和 类名
----------------------------

Namespaces and classes MUST follow [PSR-0].

命名空间和类必须遵守 [PSR-0]。

This means each class is in a file by itself, and is in a namespace of at
least one level: a top-level vendor name.

这意味着一个源文件中只能有一个类(class)，
并且每个类至少要有一级空间名：即一个顶级的组织名。

Class names MUST be declared in `StudlyCaps`.

类名必须使用 `StudlyCaps` 写法。

Code written for PHP 5.3 and after MUST use formal namespaces.

PHP5.3之后的代码必须使用正式的命名空间。

For example:

示例：

```php
<?php
// PHP 5.3 and later:
namespace Vendor\Model;

class Foo
{
}
```

Code written for 5.2.x and before SHOULD use the pseudo-namespacing convention
of `Vendor_` prefixes on class names.

PHP5.2.x之前的代码建议用伪命名空间 `Vendor_` 作为类的前缀

```php
<?php
// PHP 5.2.x and earlier:
class Vendor_Model_Foo
{
}
```

4. Class Constants, Properties, and Methods
-------------------------------------------

4. 类的常量，属性，和方法
-------------------------------------------

The term "class" refers to all classes, interfaces, and traits.

术语“类”指类（class），接口（interface），和 特性（traits）。

### 4.1. Constants

### 4.1. 常量

Class constants MUST be declared in all upper case with underscore separators.

类常量必须只由大写字母和下划线组成。

For example:

示例：

```php
<?php
namespace Vendor\Model;

class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';
}
```

### 4.2. Properties

### 4.2 属性

This guide intentionally avoids any recommendation regarding the use of
`$StudlyCaps`, `$camelCase`, or `$under_score` property names.

本指南中故意不对 `$StulyCaps`，`$camelCase`
或者 `$unser_score` 中的某一种风格作特别推荐，
完全由读者依据个人喜好决定属性名的命名风格。

Whatever naming convention is used SHOULD be applied consistently within a
reasonable scope. That scope may be vendor-level, package-level, class-level,
or method-level.

但是不管你如何定义属性名，建议在一个合理的范围内保持一致。
这个范围可能是组织级别的，包级别的，类级别的，或者方法级别的。

### 4.3. Methods

### 4.3 方法

Method names MUST be declared in `camelCase()`.

方法名则必须使用 `camelCase()` 风格来声明。