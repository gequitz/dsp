## Installing the necessary packages

You will first install some important packages. A lot of this involves
typing commands in the terminal. (In case you haven't used the
terminal in a Mac OS X before, you can open it by holding down
Command, hitting Space, typing terminal, and clicking on the terminal
application that looks like a black box)


### Apple's Xcode and Command Line Tools

Xcode is the developer's suite for OSX that comes free from Apple,
however, it doesn't come installed by default. Command Line Tools is a
part of it that makes the OS X command line behave more like Unix.
Since OSX Lion, the Xcode installation doesn't include the command
Line Tools by default.


###### On Mac OS X Lion / Mountain Lion

You can install Xcode via the
[App Store](https://itunes.apple.com/us/app/xcode/id497799835).

Once Xcode has been installed, run Xcode and then open the
preferences. Select the Download section and the Components tab and
install Command Line Tools from there.

###### On Mavericks / Yosemite

You can install Command Line Tools directly on a terminal with

```bash
xcode-select --install
```

### Homebrew

Homebrew is an excellent package manager for OSX. If you don't have
it, install it with

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Open the `.bash_profile` file in your home directory (create one if it
doesn't exist) and add this line:

```bash
export PATH=/usr/local/bin:/usr/local/share/python:$PATH
```

Homebrew installs packages in `/usr/local` and this makes sure you can
run these packages from the command line. To apply this change, do

```bash
source ~/.bash_profile
```

Or alternatively, close the terminal and open a new one.


### Python

We will use homebrew to install python. OS X comes with python, but
it's runtime environment is not up to date. Install python with

```bash
brew install python
```

This may take a while. Now when you do

```bash
which python
```

you should see

```bash
/usr/local/bin/python
```

### Pip

Pip is a python package manager. Install it with

```bash
easy_install pip
```

### Numpy and Scipy

Numpy and Scipy are the fundamental scientific computing packages for python.
Use pip to install them:

```bash
pip install numpy
pip install scipy
```

NOTE: If you encounter an error in either of these steps, try installing gfortran (a dependency) with homebrew:

```bash
brew install gfortran
```

and then try again. Gfortran comes with gcc, already provided by OS X, but older versions did not have it.


### iPython and iPython notebook

```bash
pip install ipython[notebook]
```


### Statsmodels

```bash
pip install statsmodels
```


### Matplotlib

```bash
brew install pkg-config
pip install matplotlib
```


###### Note

With any of these pip packages, if you already have it
installed, add an --upgrade to the end like this:

```bash
pip install matplotlib --upgrade
```

to make sure you have the latest version.


### Test that you have the right environment

Type

```bash
ipython
```

to open an ipython IDE. Then test numpy, scipy and matplotlib:

```bash
import numpy
import scipy
import statsmodels
import matplotlib
```

There shouldn't be any errors.

If for some reason you don't want to use homebrew, or you hit
unexpected problems, you can check out the alternative installation
guide (below) to reach this step.


### scikit-learn

Scikit.learn is an excellent machine learning library for python.

```bash
pip install scikit-learn
```


### Pandas is a data analysis library for python.

```bash
pip install pandas
```


### Test scikit-learn and pandas

Open up the python interpreter with

```bash
python
```

and try importing these packages

```bash
import sklearn
import pandas
```

There should be no errors.


### Git

Git is a version control tool. You can use the graphical installer
that you can download from
[here](http://sourceforge.net/projects/git-osx-installer/).

Congratulations! You are done with installing packages!


## Alternative matplotlib installation

This is another way of installing matplotlib and other packages, but
is more likely to run into problems.


### Freetype and png libraries (necessary for matplotlib)

Open a terminal and type the following:

```bash
sudo mkdir -p /usr/local/include
sudo ln -s /usr/X11/include/freetype2/freetype /usr/local/include/freetype
sudo ln -s /usr/X11/include/ft2build.h /usr/local/include/ft2build.h
sudo ln -s /usr/X11/include/png.h /usr/local/include/png.h
sudo ln -s /usr/X11/include/pngconf.h /usr/local/include/pngconf.h
sudo ln -s /usr/X11/include/pnglibconf.h /usr/local/include/pnglibconf.h

sudo mkdir -p /usr/local/lib
sudo ln -s /usr/X11/lib/libfreetype.dylib /usr/local/lib/libfreetype.dylib
sudo ln -s /usr/X11/lib/libpng.dylib /usr/local/lib/libpng.dylib
```

This puts links of these files where matplotlib looks at. The sudo
command will prompt your password. If you get errors about not finding
the files that you are trying to link to, this means you don't have
X11 installed. You can install it from
[here](http://xquartz.macosforge.org/landing/), and then repeat these
steps.


### Pip

Pip is a python package manager. Install it with

```bash
sudo easy_install pip
```


### iPython, Numpy, Scipy

Now we can use pip to install these packages

```bash
sudo pip install ipython
sudo pip install numpy
sudo pip install scipy
```


### Matplotlib

```bash
sudo pip install matplotlib
```

Note: With any of these pip packages, if you already have it
installed, add an --upgrade to the end like this:

```bash
sudo pip install matplotlib --upgrade
```

to make sure you have the latest version.

Also, here are online resources that you can refer to if your setup
hits any unexpected problems:
 * [A larger stack with virtual environment](http://www.tapir.caltech.edu/~dtsang/python.html)
 * [Linking X11 method](https://github.com/rueckstiess/mtools/wiki/matplotlib-Installation-Guide)
 * [Homebrew method](http://penandpants.com/2012/02/24/install-python/)