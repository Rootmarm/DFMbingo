This is the @DFMData fork of WNYC's Bingo Card generator. A live example is here: (http://data.digitalfirstmedia.com/bingo/emmys2013/newcard.html)

Interactive Bingo Card Generator
================================

By following these step-by-step instructions, you should be able to install your own branded and customized version of WNYC's bingo card generator.

You're welcome to edit the code and insert your own images as you see fit, though WNYC asks that you leave the credits thanking their @datanews team intact. Also, it's worth noting the project includes and relies on open-source code from jQuery (http://jquery.org/license/), the Miso Project (https://github.com/misoproject/dataset) and Handlebars (https://github.com/wycats/handlebars.js/blob/master/LICENSE).

![DFM Bingo](screenshots/bingo.png)

Get Started
-----------
- Click downloads in the upper right corner here and download and extract the zip. Or run this code at the command line to get your own local copy:

```
git clone git@github.com:dfmdata/DFMbingo.git YOUR_NEW_PROJECT_NAME
```

- Figure out where the bingo game will sit on your webserver. Open your favorite text editor and search live_files/embed.html and live_files/printcard.html for the string "mysite.url" and replace with the path to your files. For instance, on our site, we would replace "mysite.url" with "project.wnyc.org/debate-bingo".

- In live_files/embed.html, live_files/newcard.html and live_files/printcard.html, replace "YOUR TITLE GOES HERE" with a title for your bingo game, like "Presidential Debate Bingo."

- In the live_files/img directory, replace "header_logo_black.png" with whatever you want to appear in the upper left of the bingo card. (Or you can delete it altogether and remove the line referencing it from printcard.html and embed.html.)

- In the live_files/embed.html, be sure to update the hashtag #debatebingo on line 156 to your new hashtag for this card. In live_files/js/this-chart.js, on line 147, change the "hashtags=debatebingo" parameter in the URL to "hashtags=emmysbingo" or whatever hashtag you want to use for the event.

Setting Up the Tiles
--------------------

The content of the tiles (or squares) is stored in a CSV called data/bingo.csv. It's a standard, spreadsheet-style comma-separated value with five columns, headed "B","I","N","G","O". The list of items under each letter should be the same length ... which means each row in the CSV should have 5 values (one for each letter). You need at least 5 rows, but can have more. The code will randomly pick from the entire list and put them in a random order.

The columns should all be the same number of terms (so same number of items on each line) and should have the text of bingo tiles you want to include in those respective columns. Like most CSVs, if there are commas or quotes in the  that if there are commas or quite.

Also note that if any item between the commas HAS a comma or a quote, you need to surround that item in quote marks. Like:

   "Obama's phone rings, has annoying Marimba sound"

And if you're actually using a quote in the item, represent those with double-double quotes, like this:

   "Obama says ""Romneycare"""

Final Polishing
---------------

-- Make any other tweaks to the HTML, CSS or graphics you want to make. You might want to change the colors, replace the donkey and elephant graphics, or drop in a custom free square.

-- Upload the contents of the live_files directory to your server. If you want to embed the bingo game on a page, use the HTML code:
```
<iframe src="http://mysite.url/embed.html" height="785" width="600" scrolling="no" frameborder="0"></iframe>
```
... replacing mysite.url with your own embed path.

Note: Because the bingo game dynamically fetches information from the CSV file from the server, it won't work if you simply open the HTML files. You have to either upload them to a server and try it from there. To simulate that locally, we use Python's built-in SimpleHTTPServer, which you can launch by running "python -m SimpleHTTPServer" in the live_files directory, then going to http://localhost:8000 in your web browser.

Notes
-----

DISCLAIMER: WNYC wrote this code very quickly and wanted to share it quickly, too. So there may be problems and pitfalls, and they can't take responsibility for it failing or causing any problems for you or your systems.

Let them know if you use or improve on it! We're interested. Tweet @datanews, send us a pull request, or email jkeefe@wnyc.org.

DFMData has fixed a couple of bugs in our version that got merged back into the original code. If you see anything else, please fork this and send a pull request and we'll send back to the original team, or you can go directly to WNYC's version at https://github.com/smelendez/bingo
