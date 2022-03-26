# html-diffchecker
This is a mix of difflibs HTML visualizer and diffchecker.com's.\
Tested on Python 3.7 and 3.10.\
It's just a modification of difflib.

## Prerequisites
```
Windows:
py -3 -m pip install ftfy

Linux:
python3 -m pip install ftfy
```

## My Usage:

```py
import mdifflib
import ftfy

# Either read it from a file:
left = open("left.txt", "r", encoding="utf-8-sig").readlines()
right = open("right.txt", "r", encoding="utf-8-sig").readlines()

diff_html = mdifflib.HtmlDiff().make_file(
  left,  # Left(old) text
  right,  # Right(new) text
  context=True,  # If this is true, only lines where modifications have been made will be shown
  numlines=3  # With this, 3 lines after and before the context will also be shown
)

diff_html = ftfy.fix_encoding(diff_html)  # Fixes encoding

with open("output.html", "w", encoding="utf-8") as f:
    f.write(diff_html)

```



You can also split a text with this instead of reading a file:
```py
import re
left = re.split("\r\n|\n", left)
```
