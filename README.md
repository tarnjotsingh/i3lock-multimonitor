# i3lock-multimonitor
This is a script which uses a background image, resizes it to show correctly on any multimonitor setup.

![i3lock-multimonitor-demo](./i3lock-multimonitor-demo.png "i3lock-multimonitor-demo.png")

The idea for this project was shamelessly copied from [guimeira](https://github.com/guimeira)'s [i3lock-fancy-multimonitor](https://github.com/guimeira/i3lock-fancy-multimonitor).

Project was forked from [ShikherVerma](https://github.com/ShikherVerma/i3lock-multimonitor) with my own personal tweaks to the lock script.

Will be looking into making an Arch Package and an RPM at some point.

It uses [ImageMagick](http://www.imagemagick.org/) to resize the [background image](./img/background.png). You can replace this image to change background.

By using information from [xrandr](http://www.x.org/wiki/Projects/XRandR/) and basic math, this script supports multiple monitor setups, displaying the background image on all screens.

It caches the generated image for different screen sizes and xrandr output. So even though first `i3lock-mm` command will take a second to finish, subsequent `i3lock-mm` will be lighting fast.

## Installation
Make sure you have all the dependencies:
Note - Instructions are for Ubuntu since its the most popular linux distro.
```
sudo apt-get install imagemagick i3lock
```
Copy the `i3lock-mm` script along with the images to some place on your system (e.g.: the i3 folder) and give it execution permission: 

OR

Copy the `i3lock-mm` into your binaries folder (reason why I made the changes)
```
git clone https://github.com/tarnjotsingh/i3lock-multimonitor.git
cp -r i3lock-multimonitor ~/.i3
chmod +x ~/.i3/i3lock-multimonitor/i3lock-mm
```
Create a key binding on your i3 config file (in this example I'm using $mod+p):
```
echo "bindsym \$mod+p exec /home/$USER/.i3/i3lock-multimonitor/i3lock-mm" >> ~/.i3/config
OR
echo "bindsym \$mod+p i3lock-mm" >> ~/.i3/config
```
Now reload the i3 configuration file. By default, the key binding is `$mod+Shift+c`.
