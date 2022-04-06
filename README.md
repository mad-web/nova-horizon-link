[![Stand With Ukraine](https://raw.githubusercontent.com/vshymanskyy/StandWithUkraine/main/banner-direct-single.svg)](https://stand-with-ukraine.pp.ua)

<p align="center">
    <img title="Nova Horizon Smart Link" height="120" src="docs/logo.png" />
</p>
<p align="center">Smart Link to <strong>Laravel Horizon Dashboard</strong> from <strong>Laravel Nova</strong></p>
<p align="center">
    <a href="https://packagist.org/packages/mad-web/nova-horizon-link"><img src="https://img.shields.io/packagist/v/mad-web/nova-horizon-link.svg" alt="Latest Stable Version"></a>
    <a href="https://styleci.io/repos/154735438"><img src="https://styleci.io/repos/154735438/shield?style=flat" alt="Code Style Status"></a>
    <a href="https://packagist.org/packages/mad-web/nova-horizon-link"><img src="https://img.shields.io/packagist/dt/mad-web/nova-horizon-link.svg" alt="Quality Score"></a>
    <a href="LICENSE.md"><img src="https://img.shields.io/badge/license-MIT-brightgreen.svg" alt="Software License"></a>
</p>

## Laravel Nova Horizon Smart Link

Ability to add link to the [Laravel Horizon](https://horizon.laravel.com/)
Dashboard in the [Laravel Nova](https://nova.laravel.com/) sidebar. Link automatically disables if current user hasn't access to the _Horizon Dashboard_ according
with access policy which is defined in `Horizon::auth` method. For more information, checkout the [documentation](https://laravel.com/docs/master/horizon#dashboard-authentication).

## Demo

<p align="center">
    <img title="Nova Horizon Smart Link Demo" height="320" src="docs/demo.png" />
</p>

## Installation

At first, install via composer:

```bash
composer require mad-web/nova-horizon-link
```

Next up, register the link in the `tools` method of the `NovaServiceProvider`:

```php
// app/Providers/NovaServiceProvider.php

// ...

public function tools()
{
    return [
        // ...
        new \MadWeb\NovaHorizonLink\HorizonLink,
    ];
}
```

## Customization

By default, link label is - **Horizon Queues**, if you prefer to customize it, just pass new label text into constructor:

```php
// app/Providers/NovaServiceProvider.php

// ...

public function tools()
{
    return [
        // ...
        new \MadWeb\NovaHorizonLink\HorizonLink('Custom Label'),
    ];
}
```

In addition, you may use _Horizon_ logo, just pass `null` or call `useLogo` method to provide more readable view:

```php
// app/Providers/NovaServiceProvider.php

// ...

public function tools()
{
    return [
        // ...

        new \MadWeb\NovaHorizonLink\HorizonLink(null),
        // or
        \MadWeb\NovaHorizonLink\HorizonLink::useLogo(),
    ];
}
```

If you need to customize link `target` attribute (for example to open a page in a new tab), just pass it as second parameter into constructor or as first parameter into `useLogo` method.
A value should be without prepended underscore `_`:

```php
// app/Providers/NovaServiceProvider.php

// ...

public function tools()
{
    return [
        // ...

        new \MadWeb\NovaHorizonLink\HorizonLink('Horizon Queues', 'blank'),
        // or
        \MadWeb\NovaHorizonLink\HorizonLink::useLogo('blank'),
    ];
}
```

If you prefer to use _Fluent Interface_:

```php
// app/Providers/NovaServiceProvider.php

// ...

public function tools()
{
    return [
        // ...

        \MadWeb\NovaHorizonLink\HorizonLink::make()->target('blank'),
        // or
        \MadWeb\NovaHorizonLink\HorizonLink::useLogo()->target('blank'),
    ];
}
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email [madweb.dev@gmail.com](mailto:madweb.dev@gmail.com) instead of using the issue tracker.

## Credits

- [Mad Web](https://github.com/mad-web)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
