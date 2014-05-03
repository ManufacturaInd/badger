badger
======

Badger is a simple text to image converter, designed to render ASCII art using bitmap fonts.

It uses [Pillow][1], the friendly PIL fork, to draw PNG images using a bitmap font in the .pil
format. Formats like BDF or PCF can be converted to the PIL font format using the ``pilfont.py``
script that comes with Pillow.

Installation
------------

You know the drill:

    sudo python setup.py install

Usage
-----

```
Usage: badger [OPTIONS] TEXTFILE

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
  -l, --list-fonts      Show available fonts and exit.
  --help                Show this message and exit.
```

Here's an example:

    badger bbs.txt --font 5x8 --leading=-1 --tracking=-1 --textcolor="#dddddd" --bgcolor="#222222"
    
...which is the same as typing:

    badger bbs.txt -f 5x8 -e -1 -r -1 -t "#dddddd" -b "#222222"

Fonts you can use
-----------------

Bitmap fonts aren't as popular now that OpenType rules modern digital typography.

There's still some good libre bitmap fonts around:

* The [X11 fonts][2]
* [PXL-2000][3]

License
-------

Badger is copylefted free software, released under the [GNU General Public License][4] v3 or any later version.


  [1]: http://pillow.readthedocs.org/en/latest/
  [2]: http://www.cl.cam.ac.uk/~mgk25/ucs-fonts.html
  [3]: http://cramer.pleintekst.nl/hacks/pxl2000/
  [4]: https://www.gnu.org/copyleft/gpl.html
