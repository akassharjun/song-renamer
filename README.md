# song-renamer
Simple python script to rename a songs's metadata using the Mutagen library.

[![CodeFactor](https://www.codefactor.io/repository/github/akassharjun/song-renamer/badge)](https://www.codefactor.io/repository/github/akassharjun/song-renamer)

## Requirements

* [Mutagen - Python Multimedia Tagging Library](https://mutagen.readthedocs.io/en/latest/)
* Python 3.5 or upwards

## How To Use

Move the `song-renamer.py` file to the directory in which you keep your songs in.

Type, and hit Enter
~~~
python3 song-renamer.py
~~~

## Sample usage of the Mutagen Library

~~~
from mutagen.id3 import ID3NoHeaderError
from mutagen.id3 import ID3, TIT2, TALB, TPE1, TPE2, COMM, TCOM, TCON, TDRC

# Read ID3 tag or create it if not present
try:
    tags = ID3(fname)
except ID3NoHeaderError:
    print("Adding ID3 header")
    tags = ID3()

tags["TIT2"] = TIT2(encoding=3, text=title)
tags["TALB"] = TALB(encoding=3, text=u'mutagen Album Name')
tags["TPE2"] = TPE2(encoding=3, text=u'mutagen Band')
tags["COMM"] = COMM(encoding=3, lang=u'eng', desc='desc', text=u'mutagen comment')
tags["TPE1"] = TPE1(encoding=3, text=u'mutagen Artist')
tags["TCOM"] = TCOM(encoding=3, text=u'mutagen Composer')
tags["TCON"] = TCON(encoding=3, text=u'mutagen Genre')
tags["TDRC"] = TDRC(encoding=3, text=u'2010')
tags["TRCK"] = TRCK(encoding=3, text=u'track_number')

tags.save(fname)
~~~
