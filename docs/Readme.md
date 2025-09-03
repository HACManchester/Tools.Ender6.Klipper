# Readme

This represents the documentation for the Hackspace Ender6 3D Printer.
This current implementation uses mkdocs to generate the site.

  * https://HACManchester.github.io/Tools.Ender6.Klipper

## Extensions

The theme in use is mkdocs-material

  * https://squidfunk.github.io/mkdocs-material/

Plugins Used:

  * https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin
  * https://github.com/mkdocstrings/mkdocstrings


## Debugging the Site

To debug / view the site locally

```sh
cd ..
mkdocs serve
```

It should then be possible to view a preview of the site at http://127.0.0.1:8000/amaranth-lang.org/


## Building the Site

To build a copy of the site for release
```sh
mkdocs build
```
