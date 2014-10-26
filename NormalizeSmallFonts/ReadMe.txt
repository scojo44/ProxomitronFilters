Normalize Small Fonts 1.2

Author:  ScoJo
Created: Nov 13 2000
Requires Proxomitron Naoko 4 beta 2+

Description:

  Resets small fonts to the "normal" size set in your browser preferences.
  Also line height is disabled to avoid text overlapping.  Large fonts are
  left alone.

What's the big deal?

  Too many web sites have their font sizes set way too small, causing
  many web surfers to increase their browser's font size defeating
  whatever purpose the small fonts have.  Maybe webmasters can read
  their web pages just fine on their 21" monitors, but have they ever
  looked at their pages on a fuzzy 15" monitor?  I've seen text in
  listboxes look smaller than the fine print in car lease ads.

  For more info read Warren Steele's "What's wrong with the FONT element?"
  here: http://www.mcsr.olemiss.edu/~mudws/font.html

Notes:

- Nowadays, Mozilla and Opera (but not Internet Explorer!) let you choose
  a minimum font size with a user-friendly interface.  I recommend using
  that feature if your browser provides it.  It will be much easier to
  pick the size you want there than to modify the filters. :)

- Cascading Stylesheet help sites will be affected since the CSS filters
  aren't bound to <style> elements and style attributes.  That is, examples
  of CSS usage will be filtered so be sure to bypass Proxomitron so you'll
  get the correct code. As of this writing, the font: property doesn't have
  a "nosize" value. :)

Test URLs:

  http://web.archive.org/web/20010117005100/http://web.icq.com/
  http://www.htmlhelp.com/reference/css/font/font.html
  http://www.htmlhelp.com/reference/css/font/font-size.html
  http://groups.yahoo.com/group/prox-list/files/Filters/
  - Of course, you'll need to log in to Yahoo first.

Changes:

  1.2   - Oct  7, 2003
    - The minimum size isn't so big (10pt instead of about 14pt).
    - Sizes less than 1 are filtered.
    - Possibly some minor stuff I forgot.
  1.1   - Jan 18, 2002
    - Sizes like 83.762421352345265461243512341234% in CSS are now filtered.
    - The <SMALL> filter works if it has an attribute.
    - Reformatted some of the filters to make them easier to read.
  1.0.2 - Dec 22, 2000 - Merry Christmas!
    - Now filters escaped quotes in JavaScript (<font size=\"-1\">).
    - Now filters <font size= >.  Netscape 4.7 renders it as really tiny text.
    - CSS font: is now bounded to its size value.
  1.0.1 - Nov 29, 2000
    - Added filter for disabling line-height: in CSS.
  1.0  - Nov 13, 2000
    - First release.
