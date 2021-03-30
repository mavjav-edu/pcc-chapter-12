# A Ship That Fires Bullets 
[![GG Goode Game by @MatthewHenryDesign](gg-good-game-galaga-RtpmUzMbynBeCgEa5E.gif)](https://giphy.com/gifs/gg-good-game-galaga-RtpmUzMbynBeCgEa5E)

Let’s build a game! We’ll use @Pygame, a collection of fun, powerful Python modules that manage graphics, animation, and even sound, making it easier for you to build sophisticated games. With Pygame handling tasks like drawing images to the screen, you can skip much of the tedious, difficult coding and focus on the higher-level logic of game dynamics.

In this chapter, you’ll set up Pygame and then create a ship that moves right and left, and fires bullets in response to player input. In the next two chapters, you’ll create a fleet of aliens to destroy, and then continue to make refinements, such as setting limits on the number of ships you can use and adding a scoreboard.

Restore Points ---

As you work your way through the Alien Invasion project, you'll develop a number of files that work together to create a functioning game. If you make an error somewhere, it can be difficult to know exactly where things went wrong. There are several *restore points* available for this chapter. You can use these restore points in two ways:

- **Compare your code to code that works:** You should try this first. Look at the code you have, and compare it to the corresponding restore point. You might be able to spot where your code differs, and simply correct your own code.

- **Start over from a restore point:** If you want to just start with code that works, you can make a copy of the project using a restore point and pick up from there. For example if you want to start from a working version that fires bullets, you can copy the files and directories from [restore_point_2_fires_bullets](restore_points/restore_point_2_fires_bullets) and go from there. This might be helpful if you get lost later in the project, or if you've been adding your own features and you want to go back to the book's version of the game.

There are three [restore points](chapter_12/restore_points) available for Chapter 12:

- The ship moves, which corresponds to the state of the game on page 257. This is [restore_point_1_ship_moves](chapter_12/restore_points/restore_point_1_ship_moves).
- The ship fires bullets, which corresponds to the state of the game on page 261. This is [restore_point_2_fires_bullets](chapter_12/restore_points/restore_point_2_fires_bullets).
- The ship fires only three bullets at a time, and the code has been refactored with `fire_bullets()`. This is [restore_point_3_end_chapter_12](chapter_12/restore_points/restore_point_3_end_chapter_12).

Installing Pygame ---

Pygame is usually straightforward to install, but it can get tricky depending on your operating system and the version of Python you have installed. These instructions can help you get Pygame installed quickly, so you can focus on building games.

- [A Ship That Fires Bullets](#a-ship-that-fires-bullets)
    - [Python 2.7](#python-27)
    - [Python 3](#python-3)
  - [TRY IT YOURSELF \#1](#try-it-yourself-1)
  - [TRY IT YOURSELF \#2](#try-it-yourself-2)
  - [TRY IT YOURSELF \#3](#try-it-yourself-3)

Pygame on Linux ---

### Python 2.7

If you're using your system's default version of Python 2.7, you can install Pygame using the package manager:

    $ sudo apt-get install python-pygame 
To make sure the installation worked correctly, start a Python terminal session and try to import Pygame:

    $ python     >>> import pygame     >>>

If you don't see an error message, you're ready to start building Alien Invasion.

### Python 3

Setting up Pygame for Python 3 is a two-step process; first you'll install some packages that Pygame depends on, then you'll download and install Pygame.

Run the following commands to install the packages required to run Alien Invasion. (If you use a command such as `python3.5` on your system, replace `python3-dev` with `python3.5-dev`):

    $ sudo apt-get install python3-dev mercurial     $ sudo apt-get install libsdl-image1.2-dev libsdl2-dev libsdl-ttf2.0-dev 
If you want to enable some more advanced functionality in Pygame such as the ability to add sounds, you can also install the following libraries:

    $ sudo apt-get install libsdl-mixer1.2-dev libportmidi-dev     $ sudo apt-get install libswscale-dev libsmpeg-dev libavformat-dev libavcodec-dev     $ sudo apt-get install python-numpy 
You'll need pip for the next step; if you haven't set up pip yet, see the [instructions for setting up pip](installing_pip.md). Enter the following to install Pygame:

    $ pip install --user hg+http://bitbucket.org/pygame/pygame 
The output will pause for a moment, informing you which libraries were found. Press **Enter**, even if there are some libraries missing. You should see a message that Pygame installed successfully. To confirm the installation was successful, start a Python terminal session and try to import Pygame by entering the following:

    $ python3
    >>> import pygame     >>>

If you see no error messages, you're ready to start working on Alien Invasion!

<a href='pygame_osx'></a>Pygame on OS X ---

You'll need [Homebrew](http://brew.sh) to install some packages that Pygame depends on.

To install the libraries that Pygame depends on, enter the following:

    $ brew install hg sdl sdl_image sdl_ttf 
This installs the minimum number of packages needed to run Alien Invasion. If you want Pygame to have a little more functionality such as working with sound, you can install two additional libraries:

    $ brew install sdl_mixer portmidi 
You'll need [pip](installing_pip.md) to install Pygame. Once you have pip set up correctly, issue the following command:

    $ pip3 install --user  hg+http://bitbucket.org/pygame/pygame 
To confirm the installation, start a Python terminal session and try to import Pygame:

    $ python3
    >>> import pygame     >>>

If this works, you're ready to start building Alien Invasion!

<a href='pygame_windows'></a>Pygame on Windows ---

To install Pygame on your version of Windows, find a Windows installer at [https://bitbucket.org/pygame/pygame/downloads/](https://bitbucket.org/pygame/pygame/downloads/) that matches the version of Python you're running. If you don't see an appropriate installer listed at Bitbucket, check [http://www.lfd.uci.edu/~gohlke/pythonlibs/#pygame](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pygame).

Once you've downloaded the appropriate file, run the installer if it's a *.exe* file.

If you have a file ending in *.whl*, copy the file to your project directory. You'll need [pip](installing_pip.md) set up, so if you haven't done that yet do so now. Then open a command window, navigate to the folder that you copied the installer to, and use pip to run the installer:

    > python -m pip install --user pygame-1.9.2a0-cp35-none-win32.whl 
You can test if the installation was successful by starting a new Python terminal session and trying to import Pygame:

    > python     >>> import pygame     >>>

If this works, you're ready to start building Alien Invasion!

TRY IT YOURSELF \#1
-------------------

<span id="ch12exe1"></span>**12-1. Blue Sky:** Make a Pygame window with a blue background.

<span id="ch12exe2"></span>**12-2. Game Character:** Find a bitmap image of a game character you like or convert an image to a bitmap. Make a class that draws the character at the center of the screen and match the background color of the image to the background color of the screen, or vice versa.

TRY IT YOURSELF \#2
-------------------

<span id="ch12exe3"></span>**12-3. Rocket:** Make a game that begins with a rocket in the center of the screen. Allow the player to move the rocket up, down, left, or right using the four arrow keys. Make sure the rocket never moves beyond any edge of the screen.

<span id="ch12exe4"></span>**12-4. Keys:** Make a Pygame file that creates an empty screen. In the event loop, print the `event.key`
attribute whenever a `pygame.KEYDOWN` event is detected. Run the program and press various keys to see how Pygame responds.

TRY IT YOURSELF \#3
-------------------

<span id="ch12exe5"></span>**12-5. Sideways Shooter:** Write a game that places a ship on the left side of the screen and allows the player to move the ship up and down. Make the ship fire a bullet that travels right across the screen when the player presses the spacebar. Make sure bullets are deleted once they disappear off the screen.


&nbsp; | &nbsp; | &nbsp; | &nbsp;
----|----|----|----
[&#10094; Prev](../../../pcc-chapter-11)| &nbsp; | &nbsp; | &nbsp;[Next &#10095;](../../../pcc-chapter-13)
