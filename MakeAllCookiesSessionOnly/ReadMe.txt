Make All Cookies Session Only 1.0.1

Author:  ScoJo
Created: Jan 5, 2002
Requires Proxomitron Naoko 4 beta 5+

Description:

  These filters expand on Scott R. Lemmon's session only cookie
  idea.  Now JavaScript cookies, meta cookies and the rare
  Set-Cookie: header in multipart pages will be deleted when the
  browser is closed.  Scott's header filter (taken from the
  default.cfg in Naoko 4.1) is included for completeness.

Notes:

- Let me know if you come across a site that gets a persistent
  cookie past these filters.  Microsoft.com is spared from the
  JavaScript filter because the list it uses can conflict with
  VBScript.

- CookieList points to the Allow Cookies list in the default.cfg
  included with Proxo.

- The [mJSe] keyword makes it easy to find filters that use the
  Match_JavaScript_Expr list.

Test URLs:

  JavaScript cookies:
  http://www.real.com/
  http://www.about.com/ - inserts a single quote between ';' and 'expires'

  Meta cookies:
  http://www.about.com/

Changes:

  1.0.1 - Oct 25, 2014
    - Updated the Match - JavaScript Expression list.
  1.0   - Jan 5, 2002
    - First release as a mergeable config file.