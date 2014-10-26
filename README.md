# ScoJo's Proxomitron Filters and Lists

Here are some of my filters for the [The Proxomitron](http://www.proxomitron.info/).  I originally published them on the [Proxomitron Users List](http://groups.yahoo.com/group/prox-list/) around 2000-2004.  Since then many have been superceded by browser features and add-ons.  It was a fun challenge to create patterns to match complex strings like URLs and script code.

### Filters

- __Ad Container Remover:__  Before AdBlock Plus, there was my Ad Container Remover.  It removes ads and the HTML elements that contain them so no gaps are left behind.
- __Bright Background Dimmer:__  Lowers the brightness of bright backgrounds in the body tag, tables, table cells and any other tags with a bgcolor attribute. Works with both HTML and CSS.
- __Make All Cookies Session-Only:__  Now all cookies, even those set with JavaScript, can be modified to disappear when your web browser is closed.  Modern browsers now have this option built-in.
- __Plain Text View:__  Converts plain text content to HTML to allow you to customize its appearance.  It also forces Internet Explorer to display files sent with the text/plain content-type as plain text like most other browsers do.
- __Normalize Small Fonts:__  Reset hard-to-read fonts to the "normal" size set in your browser preferences.  Another accessibility feature found in Firefox and Google Chrome.
- __Convert Text-only URLs to Links:__  This nasty-looking filter converts text-only URLs to clickable links.  URLs that shouldn't be converted are left alone.  The Linkification add-on for Firefox and Linkify Plus for GreaseMonkey are the modern versions.

### Lists

List files for use in making filters.

- __Top-Level Domains:__  A list of the top-level domains including all the country codes.  It calls itself to match subTLDs like .co.uk and .com.au.  Now out-of-date with all these new TLDs appearing in the last couple years.
- __URL Schemes:__  URL schemes are the part before the "://" in a URL.  These include the Internet protocols and other common ones.  Many more are listed on the [Official IANA Registry of URI Schemes](http://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml)
- __Space and Spacers:__  This is a list of various types of space and HTML code used just to add space to a page.  The Ad Container Remover uses this list a lot. :)

### Object-Oriented Matching

These "meta lists" are listfiles used for matching objects similar to the way meta characters are used (\n, \w, \h etc.).  They come in handy when you need to make sure what you're matching really is what you're looking for.

For example, "http://[^/]+/" will match more stuff than "http://$LST(Match__Hostname)/" because the Match__Hostname list uses the Top__Level__Domains list to only match hostnames with official TLDs.</p>

Some of the lists call themselves so remember to edit the file if you use a different listname in your config.

- __Hostname:__  Matches a hostname.  This is different from "\h", which matches the hostname of the site the current web page was downloaded from.  This list uses the Top Level Domains list.
- __IP Address:__  Matches an IP Address.
- __E-mail Address:__  Matches an e-mail address.  This list uses the Hostname and IP Address lists.
- __URLs:__  Matches entire URLs.  This one uses many of the other lists.  The Convert Text-only URLs to Links filterset includes them all.
- __JavaScript Expressions:__  Matches JavaScript code.  See the Make All Cookies Session-Only JavaScript filter for an example of its use.
