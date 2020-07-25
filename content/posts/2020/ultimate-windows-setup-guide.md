---
title: "Ultimate Windows Setup Guide"
type: post
date: 2020-07-14T14:26:59-05:00
url: /ultimate-windows-setup-guide/
image: /images/2020-thumbs/ultimate-windows-setup-guide.jpg
categories:
  - Windows
tags:
  - Powershell
draft: true
---
 This guide will walk you through a fresh Windows installation and debloat the services, tasks, and apps that are running in the background. These tweaks are for performance in mind and weaken the security of Windows in parts. You can customize the script to not have these performance tweaks.
<!--more-->

## One Command to Do Everything

```powershell
powershell -nop -c "iex(New-Object Net.WebClient).DownloadString('https://git.io/JJ8Wh')"
```

## GitHub Project for Debloating, Optimization, and Installing Programs

<https://github.com/ChrisTitusTech/win10script/tree/master>

This project was using many of the aspects of other debloat scripts, but I combined system admin scripts with it that I use to configure workstations at businesses. I also added Chocolatey package manager to the script for easy program installations.

The script will remove scheduled tasks, windows applications, install common applications (adobe reader, notepad++, java, and more), while also disabling services, and removing windows components like Cortana that are performance hogs.

## What this script does

### Main Programs and Tweaks

- Installs Chocolatey (Package Manager for Windows)
- Installs O&O Shutup 10 and Runs Recommended Settings
- Misc 3rd Party program installs (Adobe, 7-Zip, Notepad++, and Media Player Classic-HC)
- Removals all Bloatware in MS Store (Leaves Office, Snip Tool, Xbox and other Apps used for Gaming)

### Privacy Tweaks

- Disables Telemetry
- Disables Wifi Sense
- Disables Smart Screen and Web Search
- Disables App Suggestions and Activity History
- Disables Location Tracking and Maps
- Disables Feedback and Tailored Experiences
- Removal of Error Reporting, Cortana, and Advertising ID.

### Security Tweaks

- UAC Set to Low
- Disable SMB version 1
- Set Network to Private
- Disable Controlled Folder Access
- Disable Microsoft Defender (Check customization if not using another AV)
- Disable Meltdown Flag (Big performance boost for Intel Users)
- Enables F8 Boot Menu

### Service Tweaks

Various service tweaks are done and removal of resource hungry services in windows like indexing. This shouldn't impair much functionality, but you will see big performance gains from disabling many of these services. In this section I also set time to UTC, which is nice for Linux dual boot systems.

### UI Tweaks

Windows 10's user interface is a mess and has too many notifications. This removes the Action Center, LockScreen, Sticky Keys, Task View, Expands File Transfer details by default, Show all tray icons, and various other tweaks.

### Application Tweaks

This script will keep the core of Microsoft Office, but most other Microsoft products that are sideloaded are removed. OneDrive is a big one that some use, so if you want that functionality check the customization section. Most other features removed aren't used, like Internet Explorer and Work Folders.

## Customization

I encourage people to fork this project and comment out things they don't like! Here is a list of normal things people change:

- Uninstalling OneDrive (This is on in my script)
- Installing Adobe, Chocolatey, Notepad++, MPC-HC, and 7-Zip

Comment any thing you don't want out... Example:

```
########## NOTE THE # SIGNS! These disable lines This example shows UACLow being set and Disabling SMB1
### Security Tweaks ###
"SetUACLow",                  # "SetUACHigh",
"DisableSMB1",                # "EnableSMB1",

########## NOW LETS SWAP THESE VALUES AND ENABLE SMB1 and Set UAC to HIGH
### Security Tweaks ###
"SetUACHigh",
"EnableSMB1",
```

## Conclusion

This script will be great for most users out there without losing much if any functionality. I typically run this on every system I setup, but I encourage you to fork this project and make the customizations that you need. Anything is possible, and everything can be automated. Save yourself hours of time and learn how to use not only this script, but using PowerShell.

I live stream on [Twitch][1] and encourage you to drop in and ask a question. I regularly publish on [YouTube][2] and [christitus.com][3], but if you need immediate assistance, check out the Terminal Cafe with [Discord Invite Link][4].

 [1]: https://twitch.tv/christitustech
 [2]: https://www.youtube.com/c/ChrisTitusTech
 [3]: https://www.christitus.com/
 [4]: https://www.christitus.com/discord