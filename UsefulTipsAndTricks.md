# Introduction #

This page collects useful tips and tricks that can help you improve your newsbeuter experience.

## I want to have a feed that contains all unread articles of all feeds ##

This is supported since newsbeuter 0.7. All you need to do is to add the following line to your `~/.newsbeuter/urls` file:
```
"query:Unread Articles:unread = \"yes\""
```

## When I reload the Wesnoth RSS feed, it only displays one article. What is wrong? ##

The Wesnoth RSS feed http://feed43.com/wesnoth.xml is not exactly broken, but makes it very difficult to distinguish the different articles. Newsbeuter's duplicate article detection erroneously recognizes all articles as being the same. But there's a workaround: simply copy the `wesnoth.xsl` from newsbeuter's `contrib` directory to e.g. `~/bin`, install the `xmlstarlet` tool, and add the following line to your `~/.newsbeuter/urls` file:
```
"filter:xmlstarlet tr ~/bin/fixwesnoth.xsl:http://feed43.com/wesnoth.xml"in
```
This fixes the RSS feed by adding proper GUIDs to every item which then enables newsbeuter to distinguish the different articles in the feed.