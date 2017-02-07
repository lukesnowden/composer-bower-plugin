
## Composer plugin for installing Bower packages

This Composer plugin allows you to declare, manage and install front-end packages from the Bower repository on your project using Composer.

Besides managing your main application's front-end packages, **it also supports package dependencies**, i.e. other installed composer 
packages may define their own bower dependencies.

This plugin will merge all bower dependencies and generate a `bower.json` file on the root directory of your project.

> You should exclude this file from version control and you should refrain from modifying it, as you may loose any changes
you make to it.

### Configuring

Dependencies are specified by an extra configuration section on your project's `composer.json` or on any 
packages' own `composer.json`.

> `bower.json` files are neither required nor supported. This is by design. All configuration information comes from `composer.json`.

#### Supported configuration keys

1. `require`
1. `require-dev`
1. `overrides`
1. `resolutions`

#### Example

###### root composer.json

```json
"require": {
  "php-kit/composer-bower-plugin": "dev-master"
},
"extra": {
  "bower": {
    "require": {
      "bootstrap": "~3.3.5"
    },
    "require-dev": {
      "jasmine": "~2.3.4"
    },
    "overrides": {
      "datatables": {
        "main": "media/js/jquery.dataTables.js"
      }
    },
    "resolutions": {
      "ember": "1.5.1"
    },
    "exclude": [
      "semantic-ui"
    ]
  }
}
```

#### Target installation directory

The dependencies will be installed on `vendor/bower_components` by default.
You can customize that location via a `.bowerrc` file. Refer to the Bower documentation.

### Running

The plugin updates bower dependencies whenever one or more packages are installed or removed.

You may then copy the relevant source code files from the installation directory to a public web directory, using your favorite build tool.

## License

This library is open-source software licensed under the BSD-2-Clause license (see the accompanying `COPYING` file).

Copyright &copy; 2015 by Impactwave Lda <impactwave@impactwave.com>  
Copyright &copy; 2014 by Vivid Planet Software GmbH <office@vivid-planet.com>

This project started as a fork of [composer-extra-assets plugin](https://github.com/koala-framework/composer-extra-assets),
but it has been extensively modified and it is, currently, no longer compatible with it.
