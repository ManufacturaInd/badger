badger
======

Badger is a simple text to image converter, designed to render ASCII art using bitmap fonts.

It uses [Pillow][1], the friendly PIL fork, to draw PNG images using a bitmap font in the .pil
format. See below how to convert other font formats to .pil.

Installation
------------

You know the drill:

    sudo python setup.py install

Usage
-----

```
# badger --help
Usage: badger [OPTIONS] FILENAME

Options:
  -f FONT, --font=FONT  Font name to use. Use -l for a list. (default: 4x6)
  -e LEADING, --leading=LEADING
                        Extra spacing between lines. (default: 0)
  -r TRACKING, --tracking=TRACKING
                        Extra spacing between characters. (default: 0)
  -t TEXTCOLOR, --textcolor=TEXTCOLOR
                        Text color.
  -b BGCOLOR, --bgcolor=BGCOLOR
                        Background color.
  -w WIDTH, --width=WIDTH
                        Width in characters when converting images.
  -l, --list-fonts      Show available fonts and exit.
  --help                Show this message and exit.
```

Here's an example:

    badger gnu.txt --font 5x8 --leading=-1 --tracking=-1 --textcolor="#dddddd" --bgcolor="#222222"
    
...which is the same as typing:

    badger gnu.txt -f 5x8 -e -1 -r -1 -t #ddd -b #222

Note that you can use negative leading or tracking values, and specify colors by name instead of hex values (e.g. `white` or `cyan`).

Badger also works with images instead of text files, taking care of the conversion for you thanks to **jp2a** and **Imagemagick**.

    badger gavroche.png -f 10x20 --width 40


Fonts you can use
-----------------

`badger` assumes that your pil fonts will be available at `~/.badger/pil-fonts/`.

Bitmap font formats like BDF or PCF can be converted to the PIL font format using the ``pilfont.py``
script that comes with Pillow; it should be ready to use in your shell by typing `pilfont` or `pilfont.py`.

There's some good libre bitmap fonts around, we could certainly do with a bigger list:

* The [X11 fonts][2]
* [PXL-2000][3]
 

ASCII Art resources
-------------------

Some Internet history archives took care of preserving this once-vibrant form of expression.

  * [TextFiles.com](http://www.textfiles.com)
  * [Chris.com ASCII Art Collection](http://www.chris.com/ascii/)


License
-------

Badger is copylefted free software, released under the [GNU General Public License][4] v3 or any later version.


  [1]: http://pillow.readthedocs.org/en/latest/
  [2]: http://www.cl.cam.ac.uk/~mgk25/ucs-fonts.html
  [3]: http://cramer.pleintekst.nl/hacks/pxl2000/
  [4]: https://www.gnu.org/copyleft/gpl.html
