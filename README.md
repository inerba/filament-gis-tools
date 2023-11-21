# This is my package gis-tools

[![Latest Version on Packagist](https://img.shields.io/packagist/v/postare/gis-tools.svg?style=flat-square)](https://packagist.org/packages/postare/gis-tools)
[![Total Downloads](https://img.shields.io/packagist/dt/postare/gis-tools.svg?style=flat-square)](https://packagist.org/packages/postare/gis-tools)

This is where your description should go. Limit it to a paragraph or two. Consider adding a small example.

## Installation

You can install the package via composer:

```bash
composer require postare/gis-tools
```

You MUST publish assets with:

```bash
php artisan vendor:publish --tag="gis-tools-assets"
```

You can publish and run the migrations with:

```bash
php artisan vendor:publish --tag="gis-tools-migrations"
php artisan migrate
```

You can publish the config file with:

```bash
php artisan vendor:publish --tag="gis-tools-config"
```

Optionally, you can publish the views using

```bash
php artisan vendor:publish --tag="gis-tools-views"
```

This is the contents of the published config file:

```php
return [
];
```

## Usage

```php
// Form field
Map::make('location')
    ->height(500) // Altezza della mappa in px   
    ->showCoordinates() // Mostra un overlay con le coordinate del punto
    // Per definire il punto di partenza
    ->default([
        'type' => 'Point',
        'coordinates' => [
            41.72, // lng
            13.34, // lat
        ],
    ])
    // Per definire le tile da utilizzare
    // Se non specificato, usa OpenStreetMap, altrimenti una o più tile a scelta.
    // Una lista la puoi trovare qui: https://leaflet-extras.github.io/leaflet-providers/preview/
    ->tiles([
        [
            'name' => 'OpenStreetMap',
            'url' => 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
            'options' => [
                'maxZoom' => 19,
                'attribution' => 'Map data: &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors',
            ],
        ],
        [
            'name' => 'OpenTopoMap',
            'url' => 'https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png',
            'options' => [
                'maxZoom' => 17,
                'attribution' => 'Map data: &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, <a href="http://viewfinderpanoramas.org">SRTM</a> | Map style: &copy; <a href="https://opentopomap.org">OpenTopoMap</a> (<a href="https://creativecommons.org/licenses/by-sa/3.0/">CC-BY-SA</a>)',
            ],
        ],
        [
            'name' => 'Esri World Imagery',
            'url' => 'https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}',
            'options' => [
                'attribution' => '&copy; ESRI',
            ],
        ]
    ])
    // Per definire il marker, altrimenti usa quello di default
    ->markerIcon([
        'iconUrl' => 'https://mapmarker.io/api/v3/font-awesome/v6/pin?icon=fa-solid%20fa-star&size=60&color=FFF&background=990099&hoffset=0&voffset=0',
        'iconSize' => [60, 60],
        'iconAnchor' => [30, 60],
    ])
    ->required(),
```

## Testing

```bash
composer test
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [Francesco](https://github.com/postare)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
