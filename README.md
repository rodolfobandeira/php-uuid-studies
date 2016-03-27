# php-uuid-studies
Personal repository to make some experiments using UUID (all versions)

-

Examples using the library from https://github.com/ramsey/uuid

-

### Installing

1. `composer install`
2. `php uuid-test-1.php`

### Example 1:

```php
<?php
require 'vendor/autoload.php';

use Ramsey\Uuid\Uuid;
use Ramsey\Uuid\Exception\UnsatisfiedDependencyException;

try {

    // Generate a version 1 (time-based) UUID object
    $uuid1 = Uuid::uuid1();
    printf("UUID 1 (time-based): %s %s", 
        $uuid1->toString(), 
        PHP_EOL
    ); 

    // Generate a version 3 (name-based and hashed with MD5) UUID object
    $uuid3 = Uuid::uuid3(Uuid::NAMESPACE_DNS, 'rodolfo.io');
    printf("UUID 3 (name-based and hashed md5): %s %s", 
        $uuid3->toString(), 
        PHP_EOL
    ); 

    // Generate a version 4 (random) UUID object
    $uuid4 = Uuid::uuid4();
    printf("UUID 4 (random): %s %s", 
        $uuid4->toString(), 
        PHP_EOL
    );

    // Generate a version 5 (name-based and hashed with SHA1) UUID object
    $uuid5 = Uuid::uuid5(Uuid::NAMESPACE_DNS, 'rodolfo.io');
    printf("UUID 5 (name-based and hashed with SHA1): %s %s", 
        $uuid5->toString(), 
        PHP_EOL
    );

} catch (UnsatisfiedDependencyException $e) {

    // Some dependency was not met. Either the method cannot be called on a
    // 32-bit system, or it can, but it relies on Moontoast\Math to be present.
    echo 'Caught exception: ' . $e->getMessage() . "\n";

}
```


-

### To do:

- Test uuid with doctrine: https://github.com/ramsey/uuid-doctrine
