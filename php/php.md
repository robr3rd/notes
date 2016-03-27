# PHP
## Cheat Sheets
- [Index of every single example that exists in the online PHP manual (surprisingly useful when combined with CTRL+F)](http://php.net/manual/en/indexes.examples.php)
- [Index of all functions/methods](http://php.net/manual/en/indexes.functions.php)
- [Operators Precedence](http://php.net/manual/en/language.operators.precedence.php)
- [Magic Methods](http://php.net/manual/en/language.oop5.magic.php)
- Data types
	- [Primitive data types](http://php.net/manual/en/language.types.intro.php)
	- [Type casting](http://php.net/manual/en/language.types.type-juggling.php#language.types.typecasting)
	- [Type juggling](http://php.net/manual/en/language.types.type-juggling.php)
	- [Type declarations](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration) -- Note: Aside from `instanceof`-compatible types and `array` this is really only useful in >=PHP7.
	- [Type comparison tables](http://php.net/manual/en/types.comparisons.php)
- Reserved / Predefined
	- [List of Keywords](http://php.net/manual/en/reserved.keywords.php)
	- [Predefined variables](http://php.net/manual/en/reserved.variables.php) (e.g. superglobals, $argc/$argv, and so on)
	- [List of Predefined Contstants](http://php.net/manual/en/reserved.constants.php)
	- [List of Function Aliases](http://php.net/manual/en/aliases.php)
	- [List of Predefined Classes](http://php.net/manual/en/reserved.classes.php)
	- [Predefined Interfaces and Classes](http://php.net/manual/en/reserved.interfaces.php)
	- [Predefined Exceptions](http://php.net/manual/en/reserved.exceptions.php)
	- [List of Resource Types](http://php.net/manual/en/resource.php)
	- [List of "other" Reserved Words](http://php.net/manual/en/reserved.other-reserved-words.php)
- [Supported protocols and wrappers](http://php.net/manual/en/wrappers.php) -- [Context options and parameters](http://php.net/manual/en/context.php) is great supplemental reading for this
	- file:// — Accessing local filesystem
	- http:// — Accessing HTTP(s) URLs
	- ftp:// — Accessing FTP(s) URLs
	- php:// — Accessing various I/O streams
	- zlib:// — Compression Streams
	- data:// — Data (RFC 2397)
	- glob:// — Find pathnames matching pattern
	- phar:// — PHP Archive
	- ssh2:// — Secure Shell 2
	- rar:// — RAR
	- ogg:// — Audio streams
	- expect:// — Process Interaction Streams

## History
- [High-level timeline of PHP](http://php.net/manual/en/userlandnaming.globalnamespace.php)

## Style Guide
- [List of Parser Tokens](http://php.net/manual/en/tokens.php) -- Good for writing CodeSniffer rules
- [Userland Naming Guide](http://php.net/manual/en/userlandnaming.globalnamespace.php) -- Basically, "The details of how PHP handles naming scopes"

## Configuration
- [INI File Directives](http://php.net/manual/en/ini.php)
- [PHP Extensions (Categorized)](http://php.net/manual/en/extensions.membership.php)

## Reference
- Variables
	- [Variable scope](http://php.net/manual/en/language.variables.scope.php)
	- [Variable-length argument lists](http://php.net/manual/en/functions.arguments.php#functions.variable-arg-list) -- TL;DR: `function foo(...$argument) { return gettype($argument); } // array`
	- [Variable variables](http://php.net/manual/en/language.variables.variable.php)
- Type declarations (i.e. "type hinting")
	- [Argument type declarations](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict)
	- [Return type declarations](http://php.net/manual/en/functions.returning-values.php#functions.returning-values.type-declaration)
- OOP
	- [Namespaces](http://php.net/manual/en/language.namespaces.php) -- all about them
	- [Classes and Objects](http://php.net/manual/en/language.oop5.php) -- all about them
	- [Late Static Bindings](http://php.net/manual/en/language.oop5.late-static-bindings.php) -- As a quick summary, think of how ActiveRecord-style ORMs work
	- [Traits](http://php.net/manual/en/language.oop5.traits.php)
- [User-defined functions](http://php.net/manual/en/functions.user-defined.php) -- Notably, the existence/behavior of nested and conditional functions
- [Exceptions](http://php.net/manual/en/language.exceptions.php)
- [Generators](http://php.net/manual/en/language.generators.php) -- Basically, these should be used in place of long, memory-intensive loops because Generators are much more efficient
- [PHAR ("PHP Archive")](http://php.net/manual/en/intro.phar.php) -- Basically JAR files for PHP
