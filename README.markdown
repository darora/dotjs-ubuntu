..................... dotjs-ubuntu .................

dotjs-ubuntu  is a  Google Chrome  extension  that 
executes JavaScript files in `~/.js` based on their 
filename. 

  This version of dotjs is maintained for
  users under Ubuntu. The original dotjs for Mac OSX
  can be found here: `https://github.com/defunkt/dotjs`

If  you navigate to  `http://www.google.com/`, dotjs
will execute `~/.js/google.com.js`.

This makes it super  easy to spruce up your favorite
pages using JavaScript.

Bonus:  files  in `~/.js`  have jQuery 1.6.2 loaded,
regardless  of  whether  the  site  you're  hacking
uses jQuery.

Double bonus: `~/.js/default.js`  is loaded on every
request,  meaning you  can stick  plugins  or helper
functions in it.

GreaseMonkey user scripts are great, but you need to
publish them  somewhere and re-publish  after making
modifications. With dotjs, just add or edit files in
`~/.js`.

## Example

    $ cat ~/.js/github.com.js
    // swap github logo with trollface
    $('#header .logo img')
      .css('width', '100px')
      .css('margin-top', '-15px')
      .attr('src', '//bit.ly/ghD24e')

![](https://bit.ly/gAHTbC)

## How It Works

Chrome extensions can't access the local filesystem,
so dotjs  runs a tiny  web server on port  3131 that
serves files out of ~/.js.

You don't  have to worry about  starting or stopping
this web server because  we put a pretty great plist
into  ~/Library/LaunchAgents that  handles  all that
for us.

The dotjs Chrome extension then makes ajax requests
to http://localhost:3131/convore.com.js any time you
hit a page on convore.com, for example, and executes
the returned JavaScript.

## Requires

- Ubuntu
- Ruby 1.8
- rake (gem install rake)
- Google Chrome
- `/path/to/home/bin` in your $PATH

## Install

    git clone https://github.com/glenbot/dotjs-ubuntu.git
    cd dotjs-ubuntu
    rake install

After installation add the following line to your crontab

    $ crontab -e
    @reboot /path/to/home/bin/djsd -d

For the impatient run the daemon right away

    djsd -d

For the patient reboot and enjoy!

## Chromium vs Google Chrome

Multiple Chromes installed? Drag builds/dotjs.crx to
whichever is your favorite.

## Uninstall

    rake uninstall

## Credits

- Dotjs (OSX) <https://github.com/defunkt/dotjs>
- Icon: <http://raphaeljs.com/icons/>
- jQuery: <http://jquery.com/>
- Ryan Tomayko for:

> "I almost wish you could just
   stick JavaScript in ~/.js. Do
   you know what I'm saying?"

## Other Browers

- [Firefox Add-on](https://github.com/rlr/dotjs-addon)
- [Safari Extension](https://github.com/wfarr/dotjs.safariextension)
- [Fluid UserScript](https://github.com/sj26/dotjs-fluid)
