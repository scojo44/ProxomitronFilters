Plain Text View 2.1

Author:  ScoJo
Created: 7-28-2001
Requires Proxomitron Naoko-4.1

Description:

  Plain Text View converts plain text content to HTML so custom colors
  can be applied.  It also forces Internet Explorer to display files
  sent with the text/plain content-type as plain text like most other
  browsers do.

Installation:

  Merge the PlainTextView.cfg file into your config file and put
  PlainTextView.css in Proxomitron's html directory.  You can customize
  the colors in plain text content using this stylesheet.  There is also
  a separate section for printing (the "@media print" section).

Why not just use my browser's color settings?

  Normally, the colors chosen in your web browser will be used.  However,
  if you're like me and prefer to read stuff on your monitor with a
  reverse color scheme (text is lit up instead of the background), some
  web pages will be unreadable because the colors are messed up (yellow
  text on a white background for example).  This happens when the
  background color is  specified in the web page, but not the text color.
  This is a common problem with software, too.

  Anyway, this filter allows colors for plain text to be defined
  independently from web pages.

Notes:

- A good color reference is here:
  http://www.blooberry.com/indexdot/css/syntax/units/color.htm
  The "X11 Name" section has the most named colors.

- The header at the top won't appear when the page is printed out
  (assuming your browser supports CSS2).

- These filters open plain text content to the rest of your filters.
  If a filter matches something that shouldn't, put this line in
  the beginning of the match expression:

    $IHDR(Content-Type:(^text/html; PrxOriginalType="text/plain"))
  
  Filters that use <start> and <end> should work fine.

- Internet Explorer won't just display the text/plain content-type as plain
  text like other browsers if certain HTML tags are found in the file.
  It does this even if the file extension is .txt.  IE will even try to
  display as HTML image/gif files that happen to have <html> or other tags
  in them.

How it works:

  The first filter changes the Content-Type header from text/plain to

    text/html; PrxOriginalType="text/plain"

  This allows plain text content to be treated separately from normal HTML
  content.  The second filter adds code to the beginning to display the
  file as plain text using HTML.  The remaining filters convert all double
  quotes, tag delimiters (< and >), and ampersands ('&') to HTML entities.

Test URLs:

  https://tools.ietf.org/html/rfc1149
  http://www.kibo.com/textonly.txt
  http://groups.yahoo.com/group/prox-list/files/Filters/Cosmetic/NormalizeSmallFonts.cfg
  - Log in to Yahoo first to get a text/plain file.

  http://laudanski.com/security/
  - Force Internet Explorer to display text/plain as plain text.

Changes:

  2.1  - May 22, 2002
    - Added a link at the top to save or view the page unmodified.
    - Printing HTMLized output is black ink friendly.
  2.0  - Jan 18, 2002
    - Updated for Naoko-4.1.  Byte limits set to 1.
    - Speed improved by splitting up the entity filter.
    - Simplified the "Stuff at Top" filter by moving the $IHDR() check to
      the URL box.
  1.0  - Jul 29, 2001
    - First release.