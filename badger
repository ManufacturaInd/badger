#!/usr/bin/env python

# TODO
# - add conversion to txt with jp2a
# - add another mode to generate figlet specimen
# - check if jp2a is installed
# - write simple README on usage
# - add GPL3
# - push to Github

import click

TXT_FILE = "stardark.txt"
FONT = "./pil-fonts/4x6.pil"
OFFSET = 8
FONT_DIR = "./pil-fonts/"

def list_fonts(ctx, value):
    if not value:
        return
    import glob, os
    file_list = glob.glob(os.path.join(FONT_DIR, "*.pil"))
    file_list.sort()
    from pprint import pprint
    print "Available fonts:"
    for f in file_list:
        file_name = os.path.basename(f)
        font_name = file_name.split('.')[0]
	print '    ' + font_name
    print
    ctx.exit()

@click.command()
@click.argument("textfile")
@click.option('-f', '--font', default="4x6", help='Font name to use. Use -l for a list. (default: 4x6)', required=False)
@click.option('-e', '--leading', default="0", help='Extra spacing between lines. (default: 0)', type=click.INT)
@click.option('-r', '--tracking', default="0", help='Extra spacing between characters. (default: 0)', type=click.INT)
@click.option('-t', '--textcolor', default="#000000", help='Text color.', required=False)
@click.option('-b', '--bgcolor', default="#ffffff", help='Background color.', required=False)
@click.option('-l', '--list-fonts', is_flag=True, help='Show available fonts and exit.', callback=list_fonts,
              expose_value=False, is_eager=True)
def txt2img(textfile, font, offset=8, leading=0, tracking=0, size=(640, 480), bgcolor="#ffffff", textcolor="#000000"):
    from PIL import Image, ImageFont, ImageDraw
    fontpath = "./pil-fonts/%s.pil" % font
    font = ImageFont.load(fontpath)
    text = open(textfile, 'r')
    lines = text.readlines()

    # determine font sizes
    fw, fh = font.getsize('M')
    # get total text size for canvas sizing
    # w, h = font.getsize(content)
    # print w,h
    
    # find longest line to determine width
    l = max(lines, key=len)
    # this beautiful snippet came from http://stackoverflow.com/a/873333

    width, line_height = font.getsize(l)
    height = line_height*len(lines) + int(tracking)*len(lines)

    image = Image.new("RGBA", (width, height), color=bgcolor)
    draw = ImageDraw.Draw(image)
    i = 0
    for line in lines:
        if not tracking:
            draw.text((10, i), line, font=font, fill=textcolor)
        else:
            # applying tracking requires char by char output
            char_count = 0
            for char in line:
                draw.text((char_count*(fw+int(tracking)), i), char, font=font, fill=textcolor)
                char_count += 1
        i += fh + int(leading)
    try:
        image.save("result.png")
    except SystemError:
        print "Failed while trying to save image with dimensions %dx%d. Traceback follows." % (width, height)
        print
        raise


if __name__ == "__main__":
    txt2img()
