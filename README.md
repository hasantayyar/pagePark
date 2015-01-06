PagePark
========

I wrote this simple HTTP server to park domains I've bought but not yet used.

It's written in JavaScript and runs in Node.js.

Each domain is in its own folder. The content for that domain is in the folder. I went a little wild with content types, it can serve Markdown docs, or run JS code. Yet it's still very simple. Which is the point. ;-)

It's 90 percent of what all web servers do, so if you learn how to run <a href="http://pagepark.io/">PagePark</a>, you're learning how to run a web server. A real one you can use to host your sites. And it's easy to hack the code if you want to.

#### How to

1. Create a folder to host your website. 

2. Create a sub-folder named *domains*.

2. Copy pagepark.js into that folder, and run it: node pagepark.js

#### How it works

1. PagePark will automatically create a *prefs* sub-folder. 

2. Add your web content under domains. Each folder's name is the name of a domain. The contents within the folder are what we serve. <a href="http://scripting.com/2015/01/04/pageParkFolderScreenShot.png">Screen shot</a>.

3. Serves all major media types including audio and video. Files whose names end with .md are passed through the built-in Markdown processor. Files ending with .js are interpreted as scripts. The text they return is what we serve.

4. The prefs folder contains a file of settings you can change, prefs.json. These include the port that the server runs on and the name of the index file (see below).

5. stats.json contains information generated by the server including the number of times the server has started, how many hits it's received (all time and today), and hits by domain.

6. mdTemplate.txt is the template we use to serve Markdown text. You can edit this file to provide a common template for all your Markdown documents.

7. If a request comes in for a folder, we scan the folder for a file whose name begins with *index* and serve the first one we find. So the index file can be HTML, Markdown or a script, or any other type PagePark can serve. 

8. If you want to run PagePark from a folder different from the one that contains the app, set the *pageparkFolderPath* environment variable to point to that folder. 

9. There are three special endpoints on all domains: /version, /now and /status that return the version of PagePark that's running, the time on the server and the stats and prefs. 

#### Screen shot

Here's a <a href="http://scripting.com/2015/01/04/pageParkFolderScreenShot.png">screen shot</a> of my PagePark server folder. 

#### Example pages

http://noderunner.org/ -- simple home page

http://lucky.wtf/ -- images

http://lucky.wtf/test.md -- markdown page

http://lucky.wtf/badass/ -- index file in a sub-directory

http://lucky.wtf/badass/butt.js -- a page implemented in a script

http://pagepark.io/ -- the home page for this product, served by the product

http://karass.co/nosuchfile.html -- file not found

http://pagepark.io/version -- the version of PagePark that's running on the server

http://pagepark.io/now -- the time on the server

#### JavaScript sample code

I've iterated over the code to try to make it good sample code for JavaScript projects. 

I wanted to make code that could be used for people who are just getting started with Node, to help make the process easier.

There will always be more work to do here. ;-)

#### Questions, comments?

Please post a note on the <a href="https://groups.google.com/forum/#!forum/server-snacks">Server Snacks</a> mail list. 
