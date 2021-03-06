The Brill *Encyclopædia of Islam* CD-ROM edition (2003) uses a custom font in which regular characters are replaced with the glyphs they need for transcription.
The articles themselves are encoded in Win-1252, and the font is switched to this special font (Baskerville for Brill 02) as needed, using CSS.
With modern stuff like webfonts the custom font could be included for machines that don't have this font installed, but copypasting from the articles would still result in a mess, and it just doesn't feel right, so I wrote a shitty script to convert them into proper Unicode. I opted for replace() instead of tr because some characters need to be replaced with a regular letter and combining diacritics, and that's two separate characters from the Unicode/Python point of view.
The script loads the article file (actually any file fed to it as a command line argument), makes the replacements, and writes it back to the same path. This is to make batch conversion easier.
On top of that, it expects some work to be done prior to running it, namely converting form tags into spans. For some reason, form tags are preceded and followed by line breaks when displayed in a modern browser, and that disrupts the wholeness of the paragraph.
And before that, you need to unpack the html, which on the CD is compressed using bz2.

P.S. if anyone knows the more proper replacement for some of the characters, especially "j underscore" which I replaced with j-macron below - I'd be glad to fix that.
I'm also not sure if the Ba00/Ba01 fonts include something other than regular Win-1252 (it didn't seem so to me, the Ö's etc. are displayed properly with other fonts) - if so, I'll create another "conversion table" for those too.
