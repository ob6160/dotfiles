# swaylock-fancy-multimonitor
The idea for this project was shamelessly copied from [meskarune](https://github.com/meskarune)'s [i3lock-fancy](https://github.com/meskarune/i3lock-fancy).

It uses swaygrab to take a screenshots of every screen, then [ImageMagick](http://www.imagemagick.org/) blurs the image and adds a lock icon and text.

By using information from `swaymsg -t get_outputs` and basic math, this script supports multiple monitor setups, displaying the icon and text centered on all screens.

The lock icon is different from the original project, with a transparent black circle around it. The text is also an image, making it easier to customize (and to put it at the correct position). Finally, it uses vanilla [i3lock](https://github.com/i3/i3lock) instead of [i3lock-color](https://github.com/eBrnd/i3lock-color). The author of i3lock-color [is not maintaining it anymore](https://github.com/eBrnd/i3lock-color/issues/6). If you want to customize the colors of i3lock, the recommended version of i3lock-color is [this one](https://github.com/Arcaena/i3lock-color), maintained by [Chris Guillott](https://github.com/Arcaena).

## Installation
Make sure you have all the dependencies:

```
sudo apt-get install sway imagemagick jq
```

Copy the `lock` script along with the images to some place on your system (e.g.: the sway folder) and give it execution permission:

```
git clone https://github.com/sainoba/swaylock-fancy-multimonitor.git
cp -r swaylock-fancy-multimonitor ~/.sway
chmod +x ~/.sway/swaylock-fancy-multimonitor/lock
```

Create a key binding on your sway config file (in this example I'm using $mod+p):

```
echo "bindsym \$mod+p exec /home/<your username>/.sway/swaylock-fancy-multimonitor/lock" >> ~/.sway/config
```

Now reload the sway configuration file. By default, the key binding is `$mod+Shift+c`.

## Command line parameters

`-n` or `--no-text`: hide the "Type password to unlock" text.

`-p` or `--pixelate`: pixelate the background instead of blurring it. Might be faster.
