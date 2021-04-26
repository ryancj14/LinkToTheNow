# Mac Stuff

### Finder

SHIFT+COMMAND+H – opens the Home directory in finder

When in the Home directory, click File > Add to Sidebar, to make it available from the sidebar

***

### Updating

My mac seems to have a problem updating. If it doesn't work, make sure you have enought space for it first and then if it still doesn't work (restarts but doesn't install), you can try this:

...  (Actually haven't found a solution yet)

***

### Moving Windows Between Desktops

When you swipe up to see all your open windows, you can drag a window to the top to move it into another desktop.

Then use (three or) four fingers to swipe between desktops.

***

### Swiping Shortcuts

There are actually lots of swiping shortcuts that I like and that I've become used to, so these are my checked options in Settings:

![macstuff-1](https://github.com/ryancj14/LinkToTheNow/wiki/Images/MacStuff-1.png)
![macstuff-2](https://github.com/ryancj14/LinkToTheNow/wiki/Images/MacStuff-2.png)

***

### Seeing hidden folders in Finder

Within Finder, use `command`+`shift`+`.` to be able to view hidden folders and files.

Usually you only need to interact with hidden files from the terminal (using `ls -a` to see all files) but if you do need them from Finder, that is how. Then you can use that same shortcut to hide them again.

***

## Screenshots

The normal ways to take screenshots are `shift`+`command`+`4` or `shift`+`command`+`5`. However if you need another way, then here you go:
```
screencapture -T 10 screenshot.jpg
```
Takes a screenshot of your screen 10 seconds after typing, saving it under the name `screenshot.jpg`. You can change this name or the length of time it waits by changing those arguments in the command. 

***

## Create a folder
Choose File > New Folder, or press `Shift`+`Command`+`N`.

***

## Clearing Caches
While using Photoshop, it told me there isn't enough scratch space on my computer. Clearing the caches appears to be the solution:

1. Open Finder
2. You may need to do `command`+`shift`+`.` from the home directory before following the rest of these steps.
2. Click `Go` from the menu at the top.
3. Hold down the `option/alt` key to reveal the hidden Library option.

![Library](https://github.com/ryancj14/LinkToTheNow/wiki/Images/MacStuff-3.png)

4. Click on Library
5. ... On second thought, it didn't work. But there are lots of cache files in there that could possibly be cleared if needed.

***
## My Custom Commands
jarvis - starts up my Immerse 2020 work websites
```bash
#Opens my work websites
function jarvis() {
        echo "\"Time to work for a living...\""
        echo -e "\\t-Tony Stark"
        sleep 4
        open -a "Google Chrome" https://docs.google.com/spreadsheets/d/1W2j4s4HYu-WqoBLJrepEsBzCwmwIQCNI4_RISpuunew/edit#gid=0
        open -a "Google Chrome" https://discord.com/channels/706971946071359538/706972041982771252
        open -a "Google Chrome" https://mail.google.com/mail
        open -a "Google Chrome" https://drive.google.com/drive/folders/14V3GIiRtgyBFTuX7derpXNd3gUBocEbj
        open -a "Google Chrome" https://github.com/byuccl/GoogleDeviceRep/wiki
        open -a "Google Chrome" https://trello.com/b/K8DpQEEB/immerse-site
}
```

friday - starts up my fun spreadsheets
```bash
#Opens my fun spreadsheets
function friday() {
        echo "Running Calculations..."
        sleep 4
        open -a "Google Chrome" https://drive.google.com/drive/my-drive
        open -a "Google Chrome" https://docs.google.com/spreadsheets/d/1yFjMPB9voyqtemXVDYSSGXYY8WnZgGebN0PYxIze6Vo/edit#gid=376148457
        open -a "Google Chrome" https://docs.google.com/spreadsheets/d/1a4quHT92s3GZ2fR9GR3NW5iKw4NDSu_dh173KMg27hE/edit#gid=1789272768
        open -a "Google Chrome" https://docs.google.com/spreadsheets/d/1gJC1TUTwrdl0sio4Xv_PxA1HJQrEws_e1Eh0pvKP2I0/edit#gid=1423412127
        open -a "Google Chrome" https://docs.google.com/spreadsheets/d/1NHCSSYmzQ-2YdOrUZeMrsrvYriqPHwIYDU1YtddXoTg/edit#gid=967741890
        open -a "Google Chrome" https://docs.google.com/document/d/1PuKW3KiwIdnZGrN-kOY9ck0LoCEVov7Uc3LxnRSg7hE/edit
        open -a "Google Chrome" https://docs.google.com/document/d/1lNPmhxesOx6RwfOcwK-uuXIt8Oso06UAS7Jgk9St4tM/edit
        open -a "Google Chrome" https://docs.google.com/spreadsheets/d/11o16n8cR5XM_2Js3tjYJ_Sl-zGGTwa0G2vUi6roJiqY/edit#gid=852886442
}
```

----------------------------------
Initially created by Ryan Johnson, June 2020.