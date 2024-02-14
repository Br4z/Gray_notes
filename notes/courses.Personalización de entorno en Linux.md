---
id: 6cy4msxe9b2dsrqcjplh38k
title: Personalización de entorno en Linux
desc: ''
updated: 1706318494145
created: 1705187828023
---

1. xorg ly, xrandr, rofi, Kitty, polybar, bspwm and sxhkd installation: `sudo pacman -S xorg ly xrandr rofi kitty polybar bspwm sxhkd`.

2. Creation of configuration directories: `mkdir -p ~/.config/{kitty,polybar,bspwm,sxhkd}`.

3. Coping default configurations.

	```BASH
	cp /etc/polybar/config.ini ~/.config/polybar
	cp /usr/share/doc/bspwm/examples/bspwmrc ~/.config/bspwm/
	cp /usr/share/doc/bspwm/examples/sxhkdrc ~/.config/sxhkd/
	```

4. Setting the rofi menu and kitty terminal.

	```
	# terminal emulator
	super + Return
		kitty

	# program launcher
	super + @space
		rofi -show drun
	```

5. Making the `bspwmrc` script executable: `chmod u+x ~/.config/bspwm/bspwmrc`.

6. Creating the polybar launch script.

	```BASH
	touch ~/.config/polybar/launch.sh
	chmod u+x ~/.config/polybar/launch.sh
	```

	Add the following to the `launch.sh`:

	```BASH
	#!/usr/bin/env bash

	polybar-msg cmd quit

	# Launch bar1
	polybar bar1 2>&1 | tee -a /tmp/polybar1.log & disown
	```

	> `bar1` is the default bar in the default configuration file, so if you name your bar with another name, you must put that name there.

7. picom and nitrogen installation: `sudo pacman -S picom nitrogen`.

8. Adding our apps to the `bspwmrc`.

	```
	$HOME/.config/polybar/launch.sh &
	picom -f &
	nitrogen --restore &
	```

9. Installing a Nerd Font.

	1. Download the desired Nerd Font in the [page](https://www.nerdfonts.com/font-downloads).

	2. Unzip the zip file.

	3. Copy the font family into `~/local/share/fonts`.

		> Create the directories if you do not have them (`mkdir -p ~/local/share/fonts`).

I will use my normal configuration for the rest of the applications (video player, image viewer, editor...).