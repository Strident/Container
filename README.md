#Container
[![Build Status](https://img.shields.io/travis/Strident/Container.svg)](https://travis-ci.org/Strident/Container) 
[![Coverage](https://img.shields.io/codeclimate/coverage/github/Strident/Container.svg)](https://codeclimate.com/github/Strident/Container)
[![Code Climate](https://img.shields.io/codeclimate/github/Strident/Container.svg)](https://codeclimate.com/github/Strident/Container)

Dependency injection container component designed for ease of use and speed. Built for Trident. Heavily inspired by [Pimple][1].

##Installation

Installation is available via Composer. Add the package to your composer.json:

```
$ composer require strident/container ~2.0
```

##Usage

The container is incredibly simple to instantiate. Simply do the following:

```php
use Strident\Container\Container;

$container = new Container();
```

###Defining Services

From there, you can define services like so:

```php
// 'Service' class defined somewhere, and 'dependency_name' service defined

$container->set("service_name", function($container) {
    return new Service($container->get("dependency_name"));
});
```

The services are lazy loaded (i.e. nothing is instantiated until it is called).

###Extending a Service After Definition

You may also extend services once they have been defined (for example, if you wish to augment a service, alter settings, swap out dependencies etc). But note that once a service is used, it becomes locked and cannot be modified further.

```php
$container->extend("service_name", function($service, $container) {
    $service->doSomething();
    $service->addSomething($container->get("dependency_name"));
    
    return $service;
});
```

###Defining Factory Services

If you wish to return a new instance of your service every time instead of the same instance, you may define a factory service like so:

```php
$container->set("service_name", $container->factory(function($container) {
    return new Service($container->get("dependency_name"));
}));
```

###Parameters

Parameters are get / set by accessing the container like an array:

```php
// Set
$container["foo"] = "A parameter can be anything";

// Get
$foo = $container["foo"];
```

[1]: https://github.com/silexphp/Pimple

