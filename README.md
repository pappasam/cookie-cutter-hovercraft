# Cookie-Cutter template for Hovercraft

This is a cookiecutter template for use with [Hovercraft!](https://github.com/regebro/hovercraft). It is fairly minimal and results in typical slideshow presentation with left to right movement. I think this is an extremely easy way to create a pretty, engaging presentation quickly.

## Dependencies

This was developed on Linux Mint 19.1. The following programs are required to make it run in its development environment.

* [cookiecutter](https://cookiecutter.readthedocs.io/en/latest/)
* [poetry](https://poetry.eustace.io/) to manage python dependencies
* [make](https://www.gnu.org/software/make/) to orchestrate the build
* [plantuml](http://plantuml.com/) to help with diagrams
* [pandoc](https://pandoc.org/) to create a PDF
* [libsvgbin](https://wiki.gnome.org/Projects/LibRsvg) to convert svg images to png (for PDF output)
* [wget](https://www.gnu.org/software/wget/) to download web assets for offline viewing
* [pdfjam](https://github.com/rrthomas/pdfjam) to put more than 1 slide per page
* [gs](https://linux.die.net/man/1/gs) reduce size of final PDF output

## Usage

```bash
cookiecutter gh:pappasam/cookiecutter-hovercraft
```

There will be an echoed message instructing you to perform additional steps.

## Written by

Samuel Roeca *samuel.roeca@gmail.com*
