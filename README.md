Tarantool connector for yii2 framework
======================================
[![Latest Stable Version](http://poser.pugx.org/mhthnz/yii2-tarantool/v)](https://github.com/mhthnz/yii2-tarantool/releases/latest)
[![Latest Unstable Version](http://poser.pugx.org/mhthnz/yii2-tarantool/v/unstable)](https://packagist.org/packages/mhthnz/yii2-tarantool#dev-master)
![Master Branch Tests](https://github.com/mhthnz/yii2-tarantool/actions/workflows/php.yml/badge.svg?branch=master)

[Tarantool](https://www.tarantool.io/en/doc/latest/) connector for yii2 framework. Allow to use framework abstractions such as ActiveRecord, Schema, TableSchema, Query, ActiveQuery and etc using tarantool database.

Documentation is here: [docs/README.md](docs/README.md)

Reqirements
------------

![Packagist PHP Version Support](https://img.shields.io/packagist/php-v/mhthnz/yii2-tarantool)
![Tarantool version](https://img.shields.io/badge/tarantool-%3E%3D%202.4.1-blue)
![Yii2 version](https://img.shields.io/badge/yii2-%3E%3D%202.0.14-blue)

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist mhthnz/yii2-tarantool "*"
```

or add

```
"mhthnz/yii2-tarantool": "*"
```

to the require section of your `composer.json` file.

Configuration
------------
* [Dsn options](https://github.com/tarantool-php/client#dsn-string)
```php
return [
    'components' => [
        // Tarantool connection setup
        'tarantool' => [
            'class' => \mhthnz\tarantool\Connection::class,
            'dsn' => 'tcp://username:password@localhost:3301/?connect_timeout=5.0&max_retries=3',
        ],
        
    ],
    
    'bootstrap' => ['debug'],
    
    'modules' => [
        //Debug panel setup
        'debug' => [
            'class' => 'yii\debug\Module',
            'panels' => [
                'tarantool' => [
                    'class' => \mhthnz\tarantool\debug\TarantoolPanel::class,
                    'db' => 'tarantool', // Tarantool component id
                ],
            ],
            'allowedIPs' => ['127.0.0.1', '::1'],
        ],
        
    ],
];
```

Features
------------
* Tarantool `Connection` has `Command` and `QueryBuilder`
* `ActiveRecord` models with `ActiveQuery` support
* `Schema` abstraction, `TableSchema` and `ColumnSchema`
* Model validators `UniqueValidator`, `ExistsValidator`
* Data widgets like `DetailView`, `ListView`, `GridView` using `ActiveDataProvider`
* Debug panel with explain

Future plans
------------
* Migrations
* Nosql query builder
* Lua validator
* I18n source
* Rbac db source
* Transactions
* Gii code generator (models, crud, queries)
* Connection slaves support
* Queue
* Cache
* Sessions
