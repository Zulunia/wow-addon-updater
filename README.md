# wow-addon-updater - Supports Tukui

This utility provides an alternative to the Twitch/Curse client for management and updating of addons for World of Warcraft. The Twitch/Curse client is rather bloated and buggy, and comes with many features that most users will not ever use in the first place. This utility, however, is lightweight and makes it very easy to manage which addons are being updated, and to update them just by running a python script.

## Changelog

* 1/5/2019	- Updated config.ini default WoW Addon location for BFA (\World of Warcraft\_retail_\Interface\AddOns)
			Some basic troubleshooting
			
* 7/20/2018 - Updated Tukui / ElvUI Site Handler, amended ElvUI instructions below

* 7/19/2018 - Added colored output for update and summary

* 6/30/2018 - Added license information. This shouldn't really affect anyone's use of or contributions to the project.

* 6/8/2018	- Added support for Tukui repos, as well as an option to extract the subfolder of a mod folder (see changes to Input File Format section below). Thanks to https://github.com/Fezzik for assistance with this!

* 5/20/2018 (My apologies for the wait, have finally finished classes forever) - Fixed various issues with Curse URLs and redirects, added WowAce support, better error handling. MAJOR thanks to https://github.com/zurohki for this!

* 2/27/2018 - More consistent conversion of old Curse URLs. Thanks to https://github.com/zurohki for this!

* 2/27/2018 - Added formatted table of updated addons and added comment support in the in.txt file (Will ignore lines beginning with the hash character #). Thanks to https://github.com/helpfuljohn for this!

* 2/27/2018 - Added support for Curse Projects. Thanks to https://github.com/Delduwath for this!

* 2/27/2018 - Fixed crash if any blank lines in the input file. Thanks to https://github.com/SeamusConnor for this!

* 11/17/2017- Fixed compatability issues with new CurseForge site. Also backwards-compatible with old URLs still left in the input file. Major thanks to https://github.com/lithium720 for letting me know about this (as I'm currently on an extended break from WoW) and https://github.com/adrien-martin for contributing to the fix.

* 7/2/2017	- Fixed bug that would cause the app to crash after downloading with no previous pip installations (i.e. the import errors)

## First-time setup

This utility has two dependencies:

* A version of [Python](https://www.python.org/) 3 (Any version of Python 3 should do)
* [python-pip](https://pypi.org/project/pip/) for installing the following modules 
* The [requests](http://docs.python-requests.org/en/master/) module | pip install termcolor
* The [termcolor](https://pypi.org/project/termcolor/) module | pip install colorama

Thanks to https://github.com/Saritus, the requests module is now included in the download as a package, so there is no longer any need to install those yourself. Just install Python 3, download this app, configure the utility, and double click "WoWAddonUpdater.py" to start.

## Configuring the utility

The "config.ini" file is used by the utility to find where to install the addons to, and where to get the list of mods from.

The default location to install the addons to is "C:\Program Files (x86)\World of Warcraft\Interface\AddOns". If this is not the location where you have World of Warcraft installed, you will need to edit "config.ini" to point to your addons folder.

The default location of the addon list file is simply "in.txt", but this file will not exist on your PC, so you should either create "in.txt" in the same location as the utility, or name the file something else and edit "config.ini" to point to the new file.

The "config.ini" file also has two other properties that you may not need to change. "Installed Versions File" determines where to store the file that keeps track of the current versions of your addons, and I don't recommend changing that.

The "Close Automatically When Completed" property determines whether the window automatically closes when the process completes (both successfully and unsuccessfully). It defaults to "False" so that you can see if any errors occurred. If you run this utility as a scheduled job (e.g. upon startup, every x hours, etc), we recommend changing this to "True".

## Input file format

Whatever file you use for your list of mods needs to be formatted in a particular way. Each line corresponds to a mod, and the line just needs to contain the link to the Curse or WoWInterface page for the mod. For example:

    https://www.curseforge.com/wow/addons/world-quest-tracker
    https://www.curseforge.com/wow/addons/deadly-boss-mods
    https://www.curseforge.com/wow/addons/auctionator
    http://www.wowinterface.com/downloads/info24005-RavenousMounts.html
    
    
Each link needs to be the main page for the addon, as shown above.

If you want to extract a subfolder from the default downloaded folder (typically needed with Tukui addons), add a pipe character (|) and the name of the subfolder at the end of the line. For example, the ElvUI addon can be added as follows:

    https://git.tukui.org/elvui/elvui|ElvUI
	https://git.tukui.org/elvui/elvui|ElvUI_Config

because the downloadable zip from this website contains a subfolder called "ElvUI" containing the actual mod.

## macOS Installation Instructions - Thanks to https://github.com/melwan

1. Install Python 3 for macOS
2. Run get-pip.py (Run menu > Run Module)
3. Run get-requests.py (Run menu > Run Module)
4. Edit config.ini (using TextEdit.app)
5. Create in.txt (using TextEdit.app)
6. Run WoWAddonUpdater.py (Run menu > Run Module)

The standard addon location on macOS is /Applications/World of Warcraft/Interface/AddOns

*Note: To save to a .txt file in TextEdit, go to Preferences > "New Document" tab > Under the "Format" section, choose "Plain Text".*

## Running the utility

After configuring the utility and setting up your input file, updating your addons is as simple as double clicking the "WoWAddonUpdater.py" file.

*Note: The more addons you have in your list, the longer it will take to update them... Duh.*

## Contact info

Have any questions, concerns, issues, or suggestions for the utility? Feel free to either submit an issue through Github or email me at kuhnerdm@gmail.com. Please put in the subject line that this is for the WoW Addon Updater.

## Future plans

* Make a video guide detailing all the above information

* Update to use a visual interface instead of a command-line interface

* ~~Add version checking to eliminate reinstalls of the current versions of addons~~ Thanks to https://github.com/zurohki for the code to implement this, and to https://github.com/Saritus for integrating it into the current codebase! You will now see reduced data usage of the app, and quicker update times!

* ~~Make the code structure not suck. No, seriously... it's bad...~~ Thanks to https://github.com/Saritus for the refactoring!

* ~~Add support for more addon providers (namely WoWInterface)~~ Thanks to https://github.com/Saritus for the WoWInterface support!

Thanks for checking this out; hopefully it helps a lot of you :)

## Troubleshooting
Error Traceback (most recent call last):
  File ".\WoWAddonUpdater.py", line 7, in <module>
    import SiteHandler
  File "c:\...\wow-addon-updater\SiteHandler.py", line 3, in <module>
    from termcolor import colored   # termcolor and colorama for colored output text
ModuleNotFoundError: No module named 'termcolor'

termcolor module not installed for Python
run "pip install termcolor" 

If pip isn't found, then it's not in your environment variables, 
Conforim that "C:\Python36\Scripts\" and "C:\Python36\" are in your $PATH