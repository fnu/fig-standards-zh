Autoloading Standard
====================

自动加载标准
====================

The following describes the mandatory requirements that must be adhered
to for autoloader interoperability.

下文描述了若要使用一个通用的自动加载器，你所需要遵守的规范：

Mandatory
---------

规范
---------

* A fully-qualified namespace and class must have the following
  structure `\<Vendor Name>\(<Namespace>\)*<Class Name>`
* 一个完全标准的命名空间和类的结构是这样的：`\<Vendor Name>\(<Namespace>\)*<Class Name>`

* Each namespace must have a top-level namespace ("Vendor Name").
* 每个命名空间都必须有一个顶级的空间名("组织名(Vendor Name)")。

* Each namespace can have as many sub-namespaces as it wishes.
* 每个命名空间中可以根据需要使用任意数量的子命名空间。

* Each namespace separator is converted to a `DIRECTORY_SEPARATOR` when
  loading from the file system.
* 从文件系统中加载源文件时，命名空间中的分隔符将被转换为 `DIRECTORY_SEPARATOR`。

* Each `_` character in the CLASS NAME is converted to a
  `DIRECTORY_SEPARATOR`. The `_` character has no special meaning in the
  namespace.
* 类名中的每个 `_` 都将被转换为一个 `DIRECTORY_SEPARATOR`。`_` 在空间名中没有什么特殊的意义。

* The fully-qualified namespace and class is suffixed with `.php` when
  loading from the file system.
* 完全标准的命名空间和类从文件系统加载源文件时将会加上 `.php` 后缀。

* Alphabetic characters in vendor names, namespaces, and class names may
  be of any combination of lower case and upper case.
* 组织名，空间名，类名都由大小写字母组合而成。

Examples
--------

示例
--------

* `\Doctrine\Common\IsolatedClassLoader` => `/path/to/project/lib/vendor/Doctrine/Common/IsolatedClassLoader.php`
* `\Symfony\Core\Request` => `/path/to/project/lib/vendor/Symfony/Core/Request.php`
* `\Zend\Acl` => `/path/to/project/lib/vendor/Zend/Acl.php`
* `\Zend\Mail\Message` => `/path/to/project/lib/vendor/Zend/Mail/Message.php`

Underscores in Namespaces and Class Names
-----------------------------------------

空间名和类名中的下划线
-----------------------------------------

* `\namespace\package\Class_Name` => `/path/to/project/lib/vendor/namespace/package/Class/Name.php`
* `\namespace\package_name\Class_Name` => `/path/to/project/lib/vendor/namespace/package_name/Class/Name.php`

The standards we set here should be the lowest common denominator for
painless autoloader interoperability. You can test that you are
following these standards by utilizing this sample SplClassLoader
implementation which is able to load PHP 5.3 classes.

以上是我们为实现通用的自动加载而制定的最低标准。
你可以利用能够自动加载PHP 5.3类的SplClassLoader来测试你的代码是否符合这些标准。

Example Implementation
----------------------

实例
----------------------

Below is an example function to simply demonstrate how the above
proposed standards are autoloaded.

下面是一个怎样利用上述标准来实现自动加载的示例函数。

```php
<?php

function autoload($className)
{
    $className = ltrim($className, '\\');
    $fileName  = '';
    $namespace = '';
    if ($lastNsPos = strrpos($className, '\\')) {
        $namespace = substr($className, 0, $lastNsPos);
        $className = substr($className, $lastNsPos + 1);
        $fileName  = str_replace('\\', DIRECTORY_SEPARATOR, $namespace) . DIRECTORY_SEPARATOR;
    }
    $fileName .= str_replace('_', DIRECTORY_SEPARATOR, $className) . '.php';

    require $fileName;
}
```

SplClassLoader Implementation
-----------------------------

SplClassLoader 实现
-----------------------------

The following gist is a sample SplClassLoader implementation that can
load your classes if you follow the autoloader interoperability
standards proposed above. It is the current recommended way to load PHP
5.3 classes that follow these standards.

下面的gist是一个按照上面建议的标准来自动加载类的SplClassLoader实例。
这是依据这些标准来加载PHP 5.3类的推荐方案。

* [http://gist.github.com/221634](http://gist.github.com/221634)

