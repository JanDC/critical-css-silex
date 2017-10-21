# Critical CSS (silex package)
Package, containing all the components to integrate generated automatic critical css into a silex 1.* project

# Usage

## Installation

``composer require jandc/critical-css-silex``

## Registering the twig wrapper (with post processor) and twig extension

```php
$app->register(new TwigWrapperProvider('twig', [new CriticalCssProcessor()]));

$app->extend('twig', function (Twig_Environment $twig, $app) {
    $twig->addExtension(new CSSFromHTMLExtractor\Twig\Extension());
    return $twig;
});

```

## Mark the regions of your templates with the provided blocks
```twig
{% fold %}
    <div class="my-class">
    ...
    </div>
{% endfold %}
```

## Render your pages, using the twigwrapper
```php
 $app['twigwrapper']->render('@templates/my/template.twig', ['foo'=>'bar']);
 
 ```

