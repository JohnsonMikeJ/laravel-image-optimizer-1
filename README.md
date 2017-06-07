# Laravel Imageoptimizer

[![License](https://poser.pugx.org/approached/laravel-image-optimizer/license)](https://packagist.org/packages/approached/laravel-image-optimizer)
[![Latest Stable Version](https://poser.pugx.org/approached/laravel-image-optimizer/v/stable)](https://packagist.org/packages/approached/laravel-image-optimizer)
[![Total Downloads](https://poser.pugx.org/approached/laravel-image-optimizer/downloads)](https://packagist.org/packages/approached/laravel-image-optimizer)
[![Build Status](https://travis-ci.org/approached/laravel-image-optimizer.svg)](https://travis-ci.org/approached/laravel-image-optimizer)

With this package you can easy optimize your image in **laravel 5.x** or **lumen**. Read the google instruction https://developers.google.com/speed/docs/insights/OptimizeImages about image optimize.

## Installation

Recommend convert packages:
```bash
sudo apt-get install pngquant gifsicle jpegoptim
```

- Require this package with composer:
```
composer require approached/laravel-image-optimizer
```

- After updating composer, add the ServiceProvider to the providers array in `config/app.php`
```php
Approached\LaravelImageOptimizer\ServiceProvider::class,
```

- Copy the package config to your local config with the publish command:
```
php artisan vendor:publish
```

## Demo

### Automatic ([middleware](https://laravel.com/docs/5.4/middleware))
If you want to run the ImageOptimizer automatically for all the uploaded images:
```php
Route::get('admin/image/upload', function () {
    $picture = $request->file('picture');

   ...
})->middleware(AutoImageOptimizer::class);
```

You can also add this middleware to your `app/Http/Kernel.php`.

### Manuell

On uploading a file:
```php
public function store(Request $request, ImageOptimizer $imageOptimizer)
    {
        $picture = $request->file('picture');

        // optimize
        $imageOptimizer->optimizeUploadedImageFile($picture);

        // save
        Storage::put('/my/cool/path/test.jog', File::get($picture));

        ...
    }
```

## Extension

- On-demand image manipulation [alcodo/powerimage](https://github.com/alcodo/powerimage)
- Gallery  [alcodo/gallery](https://github.com/alcodo/gallery)

## License
MIT
