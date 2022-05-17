# The missing range field for the Filament forms.

[![Latest Version on Packagist](https://img.shields.io/packagist/v/yepsua/filament-range-field.svg?style=flat-square)](https://packagist.org/packages/yepsua/filament-range-field)
[![GitHub Tests Action Status](https://img.shields.io/github/workflow/status/yepsua/filament-range-field/run-tests?label=tests)](https://github.com/yepsua/filament-range-field/actions?query=workflow%3Arun-tests+branch%3Amain)
[![GitHub Code Style Action Status](https://img.shields.io/github/workflow/status/yepsua/filament-range-field/Check%20&%20fix%20styling?label=code%20style)](https://github.com/yepsua/filament-range-field/actions?query=workflow%3A"Check+%26+fix+styling"+branch%3Amain)
[![Total Downloads](https://img.shields.io/packagist/dt/yepsua/filament-range-field.svg?style=flat-square)](https://packagist.org/packages/yepsua/filament-range-field)

## Installation

You can install the package via composer:

```bash
composer require yepsua/filament-range-field
```

Optionally, you can publish the views using

```bash
php artisan vendor:publish --tag="filament-range-field-views"
```

## Basic usage

By default the range is used to get value from 0 to 100.

```php
use Yepsua\Filament\Forms\Components\RangeSlider

...
    protected function getFormSchema(): array
    {
        return [
            ...
            RangeSlider::make('range')
            ...
        ];
    }
...
```

Defining the steps:

```php
use Yepsua\Filament\Forms\Components\RangeSlider

...
    protected function getFormSchema(): array
    {
        return [
            ...
            RangeSlider::make('range')->steps([
                'A', // should get value: 1 for the A
                'B', // should get value: 2 for the B
                'C', // should get value: 3 for the C
                'D'  // should get value: 4 for the D
            ])
            ...
        ];
    }
...
```

### Associative Array:

```php
use Yepsua\Filament\Forms\Components\RangeSlider

...
    protected function getFormSchema(): array
    {
        return [
            ...
            RangeSlider::make('range')->steps([
                '25'  => 'A', // should get value: 25  for the A
                '50'  => 'B', // should get value: 50  for the B
                '75'  => 'C', // should get value: 75  for the C
                '100' => 'D'  // should get value: 100 for the D
            ])
            ...
        ];
    }
...
```

### Hide the Step List:

```php
use Yepsua\Filament\Forms\Components\RangeSlider

...
    protected function getFormSchema(): array
    {
        return [
            ...
            RangeSlider::make('range')->steps([
                'A',
                'B',
                'C',
                'D'
            ])->displaySteps(false)
            ...
        ];
    }
...
```

**📕 Note:** The step value is defined by the first item in the steps array, Ex. => [25, 50, 75, 100] the step value should be 25. However if you need to define any other step value you can use the setter *step*.</b>

```php
    RangeSlider::make('range')->steps([
        0 => '0',
        25 => '25',
        50 => '50',
        75 => '75',
        100 => '100'
    ])->step(25)
    ...
```

The same case applies for the *min* and *max* setters:

```php
    RangeSlider::make('range')->min(25)->max(75)->step(5)
```

## Testing

```bash
composer test
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](https://github.com/spatie/.github/blob/master/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [Omar Yepez](https://github.com/oyepez003)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.