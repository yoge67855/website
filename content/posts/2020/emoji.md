---
title: "Emoji"
type: post
date: 2020-04-09T15:35:07-05:00
url: /emoji/
image: /images/2020-thumbs/emoji.jpg
categories:
  - Linux
tags:
  - Emoji
---
This article goes over installing emoji support in Linux. 
<!--more-->

## Install Packages for Emoji Support
There are a couple packages that you need to install by default in Linux to get proper emoji support and getting them to display properly. Without this support you will pull up sites and just see blocks instead of the emoji that should be there. 

Install the following package `noto-fonts-emoji`  
Arch Install: `yay -S noto-fonts-emoji`  
Debian Install `sudo apt install noto-fonts-emoji`

## Create Font Config File
While just having the above package will give most emoji support there are some sites that still won't display properly add the following file to the fontsconfig files in your config. _Note: If ~/.config/fontsconfig doesn't exists create the folder_

Minimal Install with only emoji fonts  
`~/.config/fontconfig/conf.d/01-emoji.conf`
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <!-- Use Google Emojis -->
  <match target="pattern">
    <test qual="any" name="family"><string>Segoe UI Emoji</string></test>
    <edit name="family" mode="assign" binding="same"><string>Noto Color Emoji</string></edit>
  </match>
</fontconfig>
```

Big Install with sans-serif, serif, and monospace replaced System-wide  
`/etc/fonts/conf.d/02-emoji.conf`

```
<?xml version="1.0"?>
  <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
  <fontconfig>

   <alias>
     <family>sans-serif</family>
     <prefer>
       <family>Your favorite sans-serif font name</family>
       <family>Noto Color Emoji</family>
       <family>Noto Emoji</family>
     </prefer> 
   </alias>

   <alias>
     <family>serif</family>
     <prefer>
       <family>Your favorite serif font name</family>
       <family>Noto Color Emoji</family>
       <family>Noto Emoji</family>
     </prefer>
   </alias>

   <alias>
    <family>monospace</family>
    <prefer>
      <family>Your favorite monospace font name</family>
      <family>Noto Color Emoji</family>
      <family>Noto Emoji</family>
     </prefer>
   </alias>

  </fontconfig>
```

## Using Emoji Keyboard
First install the ibus-uniemoji package or the GNOME extension if you use that Desktop Environment.  
Arch Install: `yay -S ibus-uniemoji`  
Debian Users: _(Compile from source)_ [https://github.com/salty-horse/ibus-uniemoji](https://github.com/salty-horse/ibus-uniemoji)  
Emoji [Gnome Extension Link](https://extensions.gnome.org/extension/1162/emoji-selector/)

Then simply keybind the package or extension using your settings menu or manually launch it using your launcher.  
Launch by typing: `ibus emoji`  
_Note: I have mine bound to Meta Key + a_


## Contact Me

I live stream on [Chris Titus Tech YouTube Channel][1] every Friday at 10 AM CST and archive clips to [Titus Tech Talk][2]. I also regularly publish to [christitus.com][3], but if you'd like to contact me directly or want to contribute to help keep these articles and videos being made consider joining the CTT members. 

Two Memberships exist:
- [ChrisTitus.com Members Section][4] (_CC Only_)
  - Full Archive of All Unlisted Live Streams
  - Digital Downloads with Guides and Pre-Built Images
  - Monthly Members Only Video
  - $5 Per Month (_100% of Proceeds goes to Chris Titus Tech_)
- [YouTube Chris Titus Tech Membership][5] (_All Payments Accepted_)
  - YouTube Emojis for Comments and Live Chat
  - YouTube Badges that changes based on membership time for comments and chat.
  - All YouTube comments are highlighted when I review comments daily. 
  - Immediate Access to Full Live Streams
  - $4.99 Per Month (_70% of the Proceeds goes to Chris Titus Tech_)

 [1]: https://www.youtube.com/c/ChrisTitusTech
 [2]: https://www.youtube.com/c/ChrisTitusTechStreams
 [3]: https://christitus.com/
 [4]: https://portal.christitus.com
 [5]: https://links.christitus.com/join