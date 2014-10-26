Ad Container Remover 2.4.1

Author:  ScoJo
Created: Aug 15, 2001
Requires Proxomitron Naoko 4.1+

Description:

  Removes ads and the HTML elements that contain them.  It won't remove
  elements that aren't related to the ad.  You can turn off any other
  filters that remove the types of ads matched in the ad code list and
  even enable features such as Java and Flash without being hit with ads.
  See below for a list of default filters you no longer need.

  The third filter removes the code for the [AD] strings.  Use this if
  you use an older browser, don't want to see all those <span> tags in
  the source or just don't want anything left behind. :)

Installation:

  Copy the files in the Lists folder to your Proxomitron folder and
  merge the AdContainerRemover.cfg file.  Optional:  Add the bookmarklets
  to your bookmarks if you want to easy access to the [AD] strings.

  The position of the ACR filter might not matter, since it starts matching
  stuff long before duplicated junk filters would.  For example, a "normal"
  filter would match "stuff" while the ACR would match "<container> stuff
  </container>".

The Bookmarklets:

  Use the included bookmarklets to see the [AD] strings.
  The bookmarklets.html file includes a tester so you can try them in your
  browser before adding them to your bookmarks.  They don't work in Netscape
  4.x but the display:none style will keep them hidden.

The Ad Container Toggler:

  This is a filter you can try out for fun.  With this filter, you can
  toggle ads and other junk on and off.  =)

  It doesn't replace ads with [AD] strings.  Instead, it puts the stuff it
  matched in a <span> element with the display:none style so the ad itself
  can be toggled like an [AD] string.

The Ad Header List:

  The Ad_Header list is a list of "advertisment" notifiers that usually
  sit at the top of the ad to indicate the ad is not a part of the content.
  Titles for a block of ads would also go in this list.  Headers are treated
  like an ad but the filter requires them to be inside an element so it
  won't match "advertisement" in a block of text.

Similar Filters in Default.cfg:

  This is a list of filters from the default set in the Proxomitron
  distribution that can be disabled when using the ACR.  Some of these
  are filters that kill all uses of a technology that might not be
  needed if the filters were only used to remove ads.

  The order is as they appear in the default set.

  - Banner Blaster (limit text)
  - Banner Blaster (full text)
  - Kill JavaScript Banners
  - Kill specific Java applets
  - Flash animation killer
  - Counter Killer (if you have counter servers in your ad keyword lists.)
  - Kill off-site Images
  - Kill add-on JavaScripts
  - Sound Silencer (This default filter "silences" all embedded plugins!)
  - Kill Layers

  If you believe other filters should be listed here, let me know!

The [AD] String:

  The filter replaces ads it finds with [AD] notifiers to point out where
  the ads were.  The replacement stack (\#) records the types of ads found
  and the elements found around the ad(s).  The format of the [AD] string is

    [#CodeType-AD:<InnermostElement>:<Element>:...:<OutermostElement>]

  CodeType is the way the ad was implemented.  Some examples are [IFrame-AD],
  [Script-AD], [Java-AD] and [Form-AD].  If there are a lot of nested
  elements, the [AD] string can get pretty long!  See the record below for
  an example which also shows what it looks like when ads are next to each
  other.

Record for longest [AD] string:

  I found this one in my logs but didn't record the site it came from:

  [#Link-AD:<td>
   #Link-AD:<td>:<tr>
   #Link-AD:<td>:<tr>:<table>:<td>:<tr>:<table>:<td>:<tr>
   #Link-AD:<td>
   #Link-AD:<td>:<tr>
   #Link-AD:<td>:<tr>:<table>:<td>:<tr>:<table>:<td>:<tr>
   #Link-AD:<td>
   #Link-AD:<td>:<tr>
   #Link-AD:<td>:<tr>:<table>:<td>:<tr>:<table>:<td>:<tr>
   #Link-AD:<td>
   #Link-AD:<td>:<tr>
   #Link-AD:<td>:<tr>:<table>:<td>:<tr>:<table>:<td>:<tr>
   #Link-AD:<td>:<tr>
  ]

  13 ads in 46 elements

  Previous record holder:

  [#Image-AD:<td>:<tr>:<table>:<td>:<tr>:<table>:<td>
   #Header:<b>:<font>:<td>:<tr>
   #Image-AD:<td>
   #Image-AD:<td>:<tr>
   #Image-AD:<td>
   #Image-AD:<td>:<tr>
   #Image-AD:<td>
   #Image-AD:<td>:<tr>
   #Image-AD:<td>
   #Image-AD:<td>:<tr>
   #Image-AD:<td>
   #Image-AD:<td>:<tr>:<table>:<td>:<tr>:<table>
  ]

  11 ads and one header in 30 elements on Yahoo Groups' Sign Out page at
  http://login.yahoo.com/config?logout=1  (Yahoo sends a different ad on
  each load, so the [AD] string will vary)  That's a total take-out of 42
  items!  Thanks to JarC for finding this one!

  If you find a longer one, send me the URL!

Test URLs:

  http://www.drudgereport.com/
  http://www.spaceref.com/
  http://coord.info/GCGV0P

Changes:

  2.4.1 - May 15, 2002
    - Added protection for multiline editboxes (<textarea>).
    - Some touch-ups in various places.
  2.4   - Apr 21, 2002
    - Changed the class name of the [AD] strings.  Update your bookmarklets!
    - Added a list of similar filters found in the default set.
    - Added a filter to remove the [AD] strings.
    - Added some non-advertisement matches to the Ad Code list.
    - Ad header support improved.  Now nested "click here" text will match.
    - Removed the <frame> entry from the ad code list.
  2.3   - Jan  7, 2002
    - Added support for advertisement headers.
    - Added the Ad Container Toggler filter.
  2.2.1 - Dec 10, 2001
    - Added <applet> (Java) and <object> to the Ad Container List.
    - Fixed a problem with '>' in HTML attributes.
  2.2   - Nov 20, 2001
    - Added bookmarklets to turn the [AD] strings on and off.
    - Ad container [AD] IDs now look more like HTML tags
    - Moved scripts detected by <noscript> and plugins detected by
      <noembed> to the ad container list.
    - This config file now looks for its lists in the "Lists" directory.
    - Speed Boosts:  Adjusted the filter and the "The Ad By Itself" line so
      they don't start with parentheses.
    - Moved some info from the lists in the config file.
  2.1   - Sep  4, 2001
    - Speed Boost 1:  Put calls to the ad keyword list inside $AV()
      commands.  This should also fix some match-too-much problems.
    - Speed Boost 2:  Moved $URL() checks off the first line in some
      ad code list entries to the end of the entry.  Each $URL() check
      doubled the cpu hit!
    - Added checks for <noembed> elements to ad code list.
  2.0   - Aug 21, 2001
    - Rewrote the ad container list using $NEST().  It works!
  1.0   - Sep 25, 2000
    - Early attempt.  Best I could do without the $NEST() command. :P
