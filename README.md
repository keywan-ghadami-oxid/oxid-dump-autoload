# Description

Sometimes it's helpful to have the module-chain which is saved in the oxid database in a simple php file on the disk, e.g. for running static code analysis or to tell your IDE where to find a `*_parent` class. This little Tool allows you to generate a php-file which consinst of all `class_alias` statements used inside the shop.

Could be used for example in `phpstan` like this:
```
$ cat phpstan.neon
parameters:
    level: 0
    autoload_files:
    - %currentWorkingDirectory%/vendor/autoload.php
    - %currentWorkingDirectory%/autoload.oxid.php
    - %currentWorkingDirectory%/source/oxfunctions.php
    - %currentWorkingDirectory%/source/modules/functions.php
    - %currentWorkingDirectory%/source/overridablefunctions.php
```

# Installation

```
composer require --dev alfredbez/oxid-dump-autoload
```

# Usage

Run `vendor/bin/oxid-dump-autoload` in a environment with a running shop and a database to generate a `autoload.oxid.php` inside your current working directory.

Run `vendor/bin/oxid-dump-autoload-from-metadata` if you just want to create the classnames by using the metadata directly.
You can specify a path to the metadata like so:
```
vendor/bin/oxid-dump-autoload-from-metadata path/to/metadataFolder
# e.g. vendor/bin/oxid-dump-autoload-from-metadata source/modules/vendor/module
# not vendor/bin/oxid-dump-autoload-from-metadata source/modules/vendor/module/metadata.php
```
