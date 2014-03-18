# Autoloader

# 自动加载器

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119](http://tools.ietf.org/html/rfc2119).

[RFC 2119](http://tools.ietf.org/html/rfc2119) 中的必须(MUST)，不能(MUST NOT)，
建议(SHOULD)，不建议(SHOULD NOT)，可以/可能(MAY)等关键词
将在本节用来做一些解释性的描述。

## 1. Overview

## 1. 概述

This PSR describes a specification for [autoloading][] classes from file
paths. It is fully interoperable, and can be used in addition to any other
autoloading specification, including [PSR-0][]. This PSR also describes where
to place files that will be autoloaded according to the specification.

这个 PSR 描述的是通过文件路径 [自动载入][] 类的指南。
它是完全可互操作的，可以额外使用其它的自动载入规范，
 包括 [PSR-0][] 。这个 PSR 还描述了如何规范存放文件来自动载入。

## 2. Specification

## 2. 说明

The term "class" refers to classes, interfaces, traits, and other similar
   structures.

"类" 是一个泛称；它包含类，结构，traits 以及其他类似的结构。

A fully qualified class name has the following form:

完整的类名应该类似如下范例：

        \<NamespaceName>(\<SubNamespaceNames>)*\<ClassName>

    The fully qualified class name MUST have a top-level namespace name,
    also known as a "vendor namespace".

    一个完整的类名必须有一个顶级命名空间，也就是众所周知的 "vendor namespace"。

    The fully qualified class name MAY have one or more sub-namespace
       names.

    一个完整的类名都可以有一个或多个子命名空间。

    The fully qualified class name MUST have a terminating class name.

    一个完整的类名都必须有一个终止类名。

    Underscores have no special meaning in any portion of the fully
    qualified class name.

    下划线在完整的类名任何部分是没有特殊意义。

    Alphabetic characters in the fully qualified class name MAY be any
    combination of lower case and upper case.

    一个完整的类名由大小写字母组成。

    All class names MUST be referenced in a case-sensitive fashion.

    所有的类名必须以区分大小写的方式引用

When loading a file that corresponds to a fully qualified class name ...

当加载一个文件对应一个完整的类名

    A contiguous series of one or more leading namespace and sub-namespace
    names, not including the leading namespace separator, in the fully
    qualified class name (a "namespace prefix") corresponds to at least one
    "base directory".

    一个连续的一个或多个主命名空间和子命名空间名称，
    不包括主命名空间分隔符， 在完整的类名（一个“命名空间前缀”）必须对应于至少一个“基本目录”。

    The contiguous sub-namespace names after the "namespace prefix"
       correspond to a subdirectory within a "base directory", in which the
       namespace separators represent directory separators. The subdirectory
       name MUST match the case of the sub-namespace names.

    在“命名空间前缀”后的连续子命名空间名称对应的子目录中的“基本目录”，
    其中的命名空间分隔符表示目录分隔符；
    子目录名称必须匹配的子命名空间名称；

    The terminating class name corresponds to a file name ending in `.php`.
    The file name MUST match the case of the terminating class name.

    最后的类名应该和 `.php` 文件名匹配；文件名的大小写必须匹配；

Autoloader implementations MUST NOT throw exceptions, MUST NOT raise errors
of any level, and SHOULD NOT return a value.

自动载入器的实现不能抛出任何异常，不能抛出任何等级的错误；也不能返回值；


## 3. Examples

## 3. 示例

The table below shows the corresponding file path for a given fully qualified
class name, namespace prefix, and base directory.

如下表格展示的是完整的类名与其中相关文件路径的关系：

| Fully Qualified Class Name    | Namespace Prefix   | Base Directory           | Resulting File Path
| ----------------------------- |--------------------|--------------------------|-------------------------------------------
| 完整的类名                    | 命名空间前缀       | 基础目录                 | 实际的类文件路径
| \Acme\Log\Writer\File_Writer  | Acme\Log\Writer    | ./acme-log-writer/lib/   | ./acme-log-writer/lib/File_Writer.php
| \Aura\Web\Response\Status     | Aura\Web           | /path/to/aura-web/src/   | /path/to/aura-web/src/Response/Status.php
| \Symfony\Core\Request         | Symfony\Core       | ./vendor/Symfony/Core/   | ./vendor/Symfony/Core/Request.php
| \Zend\Acl                     | Zend               | /usr/includes/Zend/      | /usr/includes/Zend/Acl.php

For example implementations of autoloaders conforming to the specification,
please see the [examples file][]. Example implementations MUST NOT be regarded
as part of the specification and MAY change at any time.

例子中的自动载入器非常适应这个指南，请查阅 [examples file][] ；但是他不能作为指南的一部分；可能随时被改变；

[autoloading]: http://php.net/autoload
[PSR-0]: https://github.com/tangrucheng/fig-standards-zh/blob/master/PSR-0.md
[examples file]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader-examples.md
