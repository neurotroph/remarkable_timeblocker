# Time Block Planning with reMarkable 2
This repository contains a custom template if you want to do time block planning with your reMarkable 2 tablet.

## Features
* 12 hours of time block planning
* space for your "daily metrics"
* space for a "daily goal"
* some space for quick notes & tasks, you need to write down

## Installation
The installation of custom templates is currently not an officially supported feature. To have a custom template available to you, you should know some basic commands for your operating system's command line. A good explanation what to do is offered in the *reMarkableWiki*: https://remarkablewiki.com/tips/templates

You can follow the following steps, if you are using macOS or Linux, but you are doing so **at your own risk**! Using the command line, you can break your reMarkable tablet beyond repair, so be careful!

0. Download the two files in this repository's subdirectory `/dist/` (one .png and one .svg file) to a folder on your computer.
1. Attach your reMarkable tablet to your computer.
2. Find your tablets IP address and SSH password by navigating to *Settings > Help > Copyrights and licenses > General information* where you need to scroll down.
3. Start your terminal app of choice, e.g. the macOS default located at `/Applications/Utility/Terminal.app`
4. Navigate to the folder where you have downloaded the files.
5. Copy the two files to your tablet using the command `scp ./Time\ Blocking.* root@<IP ADDRESS>:/usr/share/remarkable/templates/`. Remember to replace `<IP ADDRESS>` with the IP address you found on your tablet (see above).
6. Next, you need to add the template to a .json file. This involves some mingling with a command line text editor. I prefer `nano`, which I will use in the next steps. If you are a `vi` or `emacs` kind of person, you'll likely won't need this guide anyway.
7. Login to your tablet using ssh: `ssh -l root <IP ADDRESS>`, again replacing `<IP ADDRESS>` with your tablet's IP address.
8. Open the text file you need to edit using `nano /usr/share/remarkable/templates/templates.json`.
9. Make sure, that you do not have added the template to this file yet!
10. Add a new object to the JSON file. You do so, by going to the end of the file. There you will find (starting at the end and moving up) a curly bracket, a square bracket, and another curly bracket. Between this curly bracket and the square bracket, add a `,` (comma) and a new line. On this new line enter the following:
```
{
	"name": "Time Blocking",
	"filename": "Time Blocking",
	"iconCode": "\ue9c5",
	"landscape": "false",
	"categories": [
		"Life/organize"
	]
}
```
11. Save and overwrite file by pressing `[Ctrl] + [X]`, enter `y` and confirm the path by simply pressing `[Enter]`.
12. Finally, the UI by entering `systemctl restart xochitl`. Your tablet's screen will go dark and restart.
13. Now, when creating a notebook are changing a page's template, you should have a template called "Time Blocking" available. Enjoy!
