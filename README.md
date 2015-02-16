#Container
[![Build Status](https://img.shields.io/travis/Strident/Container.svg)](https://travis-ci.org/Strident/Container) 
[![Coverage](https://img.shields.io/codeclimate/coverage/github/Strident/Container.svg)](https://codeclimate.com/github/Strident/Container)
[![Code Climate](https://img.shields.io/codeclimate/github/Strident/Container.svg)](https://codeclimate.com/github/Strident/Container)

Dependency injection container component designed for ease of use and speed. Built for Trident. Heavily inspired by [Pimple][1].

##Installation

Installation is available via Composer. Add the package to your composer.json:

```
$ composer require strident/container ~1.0
```

##Usage

The container is incredibly simple to instantiate. Simply do the following:

```php
use Container\Container;

$container = new Container();
```

[1]: https://github.com/silexphp/Pimple

