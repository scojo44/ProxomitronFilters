Convert Text URLs to Links 1.0

Author:  ScoJo
Created: Dec 4 2001
Requires Proxomitron Naoko 4 beta 5+

Description:

  This filter converts text-only URLs and hostnames to clickable links.

Installation:

  If you use the "Convert Text URLs (and/or e-mail addresses) to Links"
  filters, you must use the "Protect URLs that shouldn't be converted to
  links" unless you want every URL on the page to be converted. :)

  Also, the protect filter must be at the bottom of your filter list with
  the convert filters under it.  Otherwise the protect filter will prevent
  all filters below it from matching stuff the protect filter matches.

  The convert filters are very CPU intensive so I included two versions
  of the Match_URL list, a fast one and slow one.  The fast one is set
  in this config file.  If you have an ultra fast CPU, you might want
  to try the slower list file to match hostnames, IP addresses, domain
  names by themselves as well as full URLs.  Just go to the Blockfile tab
  in the config dialog and point the Match_URL list to the slow version.
  Be warned, page loads will be slower (even on a 450Mhz Celeron CPU). =)

Using the lists as include files:

  It also demonstrates how list files can be used to create your own
  meta characters.  Several lists in this package are used as include
  files to match stuff like hostnames, IP addresses, and whole URLs.

  Besides the convert text URLs to links filters, I've included a couple
  other example filters that use the Match_URL list.  These are:

  - Grab URLs from CGI click-tracking links (header version)
  - Grab URLs from CGI click-tracking links (web filter version)

  The above two are similar to the URL Un-prefixer filters in the
  default.cfg.  I never use these because search engines usually
  have the link and an text-only URL that is made clickable. :)

  - Grab URLs from JavaScript Links

  This converts href="javascript:GoToURL('http://foo/path/file.html')"
  to a normal link.

Features of the Convert Text URLs to Links filter:

- Tags are removed for the href= URL and preserved in the link text.
- In the href= part, common entities are converted (for example, &nbsp;
  is converted to %20).
- The protocol is detected if one is not included in the URL.  For
  example, if ftp.example.com is found, the URL will start with ftp://
- Prevents matching inside tags, comments, scripts, etc.
- End of sentence punctuation at the end of a URL is left out.

Notes:

- If a web page looks messed up when a convert filter is enabled, be sure
  to load the page with HTML debug info on and search for "vert text"
  (a part of the filter's name).  Chances are, there's a URL that wasn't
  supposed to match.  Please e-mail me the URL of any pages it barfs on.

- The slow version of the Match_URL list will match stuff you didn't
  expect.  One example is version numbers with 4 segments such as Nero
  5.5.1.8.  It matches because the version number happens to be a valid
  IP address.  Another oddity is the filter will match improper
  english.It might be even be amusing.  Can you spot the hostname in
  this paragraph? :)

- The convert text URLs to links filters are disabled on Microsoft's
  site.  The Match_JavaScript_Expr list barfs on VBScript code.

- The [logspam] and [cpu] keywords make it fast and easy to disable any
  filters with these keywords in the name.  I put [logspam] on filters
  that flood the log window with filter matches and/or blockfile hits.
  As you might guess, [cpu] is for filters that eat the CPU.

- If you use a swear filter, the protect filter might be useful to
  prevent getting a 404 when going to http://foo.com/path/%#$@.html :-)

Test URLs:

- Convert Text URLs to Links:
  http://local.ptron/Test-Match-URL.html
  (put the included test file in C:\Path\to\Prox\html\)

- Grab URLs from CGI click-tracking links:
  [Defunct URL removed]

- Grab URLs from JavaScript Links:
  [Defunct URL removed]

Changes:

  1.0  - Jan 17, 2002
    - First release after many months of tweaking. =)
