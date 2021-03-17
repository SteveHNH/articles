# Getting started with bspwm on Linux

Install, configure, and start using the bspwm window manager on Fedora Linux

![BSPWM Desktop](./bspwm-desktop.png "bspwm desktop")

Some folks like to rearrange furniture. Some folks like to try new shoes, or redecorate their bedroom on the regular. Me? I try out Linux desktops.

After drooling over some of the incredible desktop environments I've seen on [Reddit](https://unixporn.reddit.com) I got curious about one window manager in particular: [bspwm](https://github.com/baskerville/bspwm). I've been a fan of the [i3](https://i3wm.org/) window manager for quite a while and I do enjoy the way everything is laid out, and the ease at getting started. But something was calling to me about bspwm. There are a few reasons I decided to try it out.

* It is _only_ a window manager
* It is managed by a few easy to configure scripts
* It supports gaps between windows by default

It simply being a window manager is probably the thing that's best pointed out about it. Like i3, there are no graphical bells and whistles applied by default. You can certainly customize it to your heart's content, but you are going to be putting in all the work to make it look exactly like you want. That's part of the appeal to me.

Though it is available on many distributions, my examples will all be with Fedora Linux.

## Installation

Bspwm is packaged in most common distributions, so all you must do is install it with your system's package manager. In the below example, we'll be installing [sxkhd](https://github.com/baskerville/sxhkd) and [dmenu](https://linux.die.net/man/1/dmenu) as well.

    dnf install bspwm sxkhd dmenu

Now you have bspwm installed, but you'll want to get going with another tool before you try to use it: sxkhd. Since bspwm is _just_ a window manager, there aren't any built in shortcuts or keyboard commands available to it. This is where it stands in contrast to something like i3. In order to get going easily, we can go ahead and configure sxkhd before we even fire up the window manager for the first time.

    systemctl start sxkhd
    systemctl enable sxkhd

That enables sxkhd at login, but we'll also need a configuration that has some basic functionality ready to go.

    curl https://raw.githubusercontent.com/baskerville/bspwm/master/examples/sxhkdrc --output ~/.config/sxkhd/sxkhdrc

It's worth taking a look at this file before we get much futher, as some commands that are called by the scripts may not exist on your system. A good example is the `super + enter` shortcut which calls `urxvt`. You should change this to your preferred terminal in the event you do not have urxvt installed.

    #
    # wm independent hotkeys
    #
    
    # terminal emulator
    super + Return
    	urxvt
    
    # program launcher
    super + @space
    	dmenu_run

That's it! If you are using GDM, LightDM, or another display manager, all you have to do is choose bspwm before logging in.

## Configuration

Once you are logged in, you'll see a whole lot of nothing on the screen. That's not a feeling of emptiness you feel. It's possibility! You are now ready to start fiddling with all the parts of a desktop environment that you have taken for granted all these years. Building from scratch is not easy, but it's very rewarding once you get the hang of it.

The most difficult thing about any window manager is getting a handle on the shortcuts. You're going to be slow to start with, but in a short time, you'll be flying around your system just using your keyboard and looking like an ultimate hacker to your friends and family.

You can tailor the system as much as you want by editing `~/.config/bspwm/bspwmrc` to add apps at launch, setup your desktops/monitors, and set rules for how your windows should behave. A few examples are set by default to get you going. Keyboard shortcuts are all managed by the sxkhdrc file.

There are plenty more open source projects to install to really get things looking nice like [feh](https://github.com/derf/feh) for desktop backroungs, [polybar](https://github.com/polybar/polybar) for that all important status bar, [rofi](https://github.com/davatorium/rofi) to really help your app launcher pop, and [compton](https://github.com/chjj/compton) to give you the shadows and transparency to get things nice and shiny.

Happy hacking!


 
