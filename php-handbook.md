# PHP Etiquette

We adopt what is seen as the industry's best practices when developing our applications. This guide explains how you can use coding standards to improve your codes readability and reusability. There’s also a set of useful tools that make adhering to these coding standards a cinch.

### Writing PSR-2

PHP Framework Interop Group has defined the coding standards PSR-2 and PSR-1 which requires the latter to comply. We use the PSR-2 coding standard with all of our projects. There’s links to the full specification below but here’s some important parts:

##### Namespaces

Every defined class must have a namespace declared if you’re working on multiple libraries it would be a good idea to establish a vendor name at the base of every namespace. For example `\Wearenext\Foobar` is be a great namespace for the Foobar project here at Next.

Composer.json might also share the base namespace in the vendor portion of its name property. Note that after each namespace declaration a new line should be made example:

```
namespace Wearenext\Clockradio;

use Carbon\Carbon;
use Wearenext\Clockradio\Radio\PlayerInterface;

class Application implements PlayerInterface
```

##### Classes

// todo: We need to put down some guide lines for example
// Do developers set out by defining namespaces for large working components
// or is it more the okay to include that in the class name. The example below could be
// written like `class Wearenext\Shop\Cart\Factory` instead of
// `class Wearenext\Shop\Factories\ShoppingCartFactory`.

When declaring a class it’s name must also be capitalized correctly. After class and methods declaration the opening and closing brace must also be on new lines. For example:

```
class ShoppingCartFactory
{
    public static function make($attributes)
    {
        return new ShoppingCart($attributes);
    }
}
```

##### Tabs vs spaces

Four Spaces, example:
```
    
```

##### Code blocks

For every other type of situation where a brace is involved the opening brace should be on the same line, examples:

```
    use Traits\Bloganaise {
        Traits\Bloganaise::create as make;
    }
    
    try {
        abort(500);
    } catch (HttpException $e) {
        //
    }
    
    If (true) {
        //
    } elseif (false) {
       //
    }
```

##### Keywords

PSR-2 requires that all PHP keywords be in lowercase at all times.
Testing with composer
We use a tool called PHP_CodeSniffer which verifies that a specified standard is correctly implemented. It’s useful to have one command to quickly verify that all the code is kosher before committing. The following composer.json defines the `composer test` command which runs the code sniffer tests:

```
{
    "name": "wearenext/foo",
    "description": "Foo project",
    "type": "project",
    "require-dev": {
        "phpunit/phpunit": "~4.0",
        "phpspec/phpspec": "~2.1",
        "squizlabs/php_codesniffer": "^2.3"
    },
    "scripts": {
        "test": "php -l -d display_errors=0 app/ && vendor/bin/phpcs -n --standard=PSR2 --report=full app/; vendor/bin/phpunit"
    }
}
```

### Links

- [PSR-2](http://www.php-fig.org/psr/psr-2/)
- [PSR-1](http://www.php-fig.org/psr/psr-1/)
- [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)

