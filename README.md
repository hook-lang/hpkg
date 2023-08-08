
# Hook's Package Manager

This is a package manager for the [Hook](https://github.com/fabiosvm/hook-lang) programming language.

> **Warning**: This package manager is still in development and is not ready for production.

## Getting started

Let's start installing the `hpkg`, and then we will install the `cowsay` package.

> **Note**: Before installing the `hpkg`, make sure you have the [Hook](https://github.com/fabiosvm/hook-lang) installed.

### Installing the package manager

The `hpkg` can be installed by just 3 steps:

1. Clone this repository in your home directory:

```
cd ~ && git clone https://github.com/fabiosvm/hpkg
```

2. Add the `hpkg/bin` directory to your `PATH`, and modify the `HOOK_PATH` environment variable:

```
echo 'export PATH="$HOME/hpkg/bin:$PATH"' >> ~/.bashrc
echo 'export HOOK_PATH="$HOOK_PATH;deps/?/src/main.hk;../deps/?/src/main.hk"' >> ~/.bashrc
```

3. Reload your shell:

```
source ~/.bashrc
```

> **Note**: The commands above are for the `bash` shell. If you use another shell, you will need to modify the commands.

### Installing a package

Now, let's install the `cowsay` package as a dependency of our project:
In your project directory, run the following command:

```
hpkg install cowsay
```

### Importing

Now, you can import the `cowsay` in your project. Put the following code in `cowsay_test.hk` file:

```js
import cowsay;

cowsay.say("Hello, world!");
```

### Running

Run your file with the `hook` command:

```
hook cowsay_test.hk
```

The output should be:

```
-----------------
< Hello, world! >
-----------------
       \   ^__^
        \  (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
```

> **Note**: For now, `install` is the only command available. To `uninstall` a package, just remove the package from the `deps` directory. More commands will be added in the future.

## Package structure

A package is a directory with the following structure:

```
package
 ├── deps
 |    └── ...
 ├── src
 |    ├── main.hk
 |    └── ...
 ├── .gitignore
 ├── LICENSE
 ├── manifest.json
 ├── README.md
 └── ...
```

### `main.hk`

Each `.hk` file is a module. The `main.hk` file is the main module of the package that will be loaded when the package is imported.
The `src` directory can contain other modules that can be imported by the `main.hk` module.

### `manifest.json`

The `manifest.json` file contains the package metadata. The `manifest.json` file must have the following structure:

```json
{
  "name": "package-name",
  "version": "1.0.0",
  "description": "Package description",
  "author": "Author name",
  "license": "MIT"
}
```

### `deps`

The `deps` directory contains the dependencies of the package. Each dependency is a directory with the same structure of a package.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
