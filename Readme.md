# Live Coding School
## March 3-8. 2020, Budapest

This is the public repository for the workshop material of the event regarding Tidal Cycles.
During this workshop you will learn:
* How to set up your computer to run Tidal Cycles
* How to make noise, create sound and even music using this Haskell-based mini-language
* How to use Tidal Cycles to generate patterns
* How to record your work
* How to use external samples and synths integrated in SuperDirt and SC3Plugins.
* Some basics of OSC messages and networked signal sending

## Installing Tidal Cycles

Installation of Tidal Cycles can be a pain in the ass even for those who are into coding a bit. Haskell is a really uncommon language and SuperCollider can cause issues as well.
This guide is to help you avoiding problems during installation.

**Please make sure that you run *everything* with administrator rights. Always.**

### Some things to note
[If you follow the official, documented methods](https://tidalCycles.org/index.php/Installation), you should have no trouble.
However, during previous workshops we have encountered several issues with installs with chocolatey on Windows, and honestly never tried installation on Mac using the `tidal-bootstrap` shell script, therefore I would not advise using them. I suggest going for the manual install, it can look a bit complicated for the first time, but
everything shall be A-OK with it.

## Install git
* You have to install **git** on your operating system, wether it is Windows, Mac or some kind of Linux.
* [You can download git from here and find some setup instructions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* Download git for your platform accordingly.
* Make sure that git is in your path and is available for programs to use it. You can achieve this by opening a bash terminal (cmd or PowerShell on Windows) and typing in the
`git --version` command. If you have successfully installed git, the terminal will promt you the installed git version accordingly.
* **Windows users, beware!** If you are using a bash-style terminal emulator like *cmder*, its internal git installation is sufficient, *you have to manually install git anyways*.

## Install SuperCollider with SuperDirt
* Download the latest stable version of SuperCollider.
* On Windows, always make sure that **you are running `scide` as a full administrator** after installation. It will have trouble with indexing help documents, accessing your network and your sound hardware etc. otherwise.
* Once SuperCollider booted, you can find a big white pane with line numbers on the left by default. This is where we can write code in SuperCollider. For using Tidal, it will be very minimal. Here you have to copy and paste the following line of code: `Quarks.checkForUpdates({Quarks.install("SuperDirt", "v1.1.1"); thisProcess.recompile()})`
* After you pasted it, you have to stand with your cursor on the line and press **shift+enter**. This will execute the command. On the right side you can track the terminal process.
* Once this is complete, you can test if SuperDirt can be run by typing the `SuperDirt.start` command and pressing **shift+enter** at the end of the line just under where you have pasted the installation command.
* If everything is ok, the SuperCollider terminal on the right will prompt you with something like `SuperDirt: listening to Tidal on port 57120`.

## Install the haskell platform with cabal
* This is an easy part, however, quite long. If you are using OSX or Linux, just go to the [haskell website and follow the setup instructions](https://www.haskell.org/platform/) for your platform. 
* **Windows users!!** [Make sure you download the proper version](https://www.haskell.org/platform/download/8.4.3/HaskellPlatform-8.4.3-full-x86_64-setup.exe) as there was a buggy one that did not work well with Tidal.
* Make sure you have **GHC** and **cabal** installed. You can do this by entering your command line and running the `ghc --v` command. If cabal is in your path, it will prompt you the version number of GHC, the glorious haskell compiler. Do the same with cabal, using the `cabal --v` command, that will give you the cabal version.
* If cabal runs perfectly, you should just type `cabal install tidal` and press enter. The process will pull all dependencies of Tidal Cycles.

## Install Atom or Visual Studio Code
* You can just simply follow the instructions from the TidalCycles website mentioned above for Atom.
* If you would rather use **Visual Studio Code** (which I strongly suggest, mostly if you would like to use Tidal as a tool in network), you can download it and find for the Tidal extension. After IDE restart, it will function automatically. You can find the extensions under the cog at the bottom left of the IDE.

## Installing SC3Plugins
SC3Plugins is an extension to SuperCollider. It is not necessary to have SC3Plugins to use Tidal Cycles, however there are lots of effects and synths that are not included in the basic SuperDirt package, and SC3 is required to use them.
* Go to the [SC3Plugins download page](https://github.com/supercollider/sc3-plugins/releases) and download the zip file with the SC3 assets that suits your OS. On Mac and Windows, it will function 100% perfectly, there is no need to build them using `make`, and the Linux tarball works usually well on Debian-based OS's.
* Find your extensions folder from SuperCollider. You have to use the `Platform.userExtensionDir` command to locate your extensions dir for your user. If you want to install the plugins system-wide, you can detect this folder using the `Platform.systemExtensionDir`. After running the command, the SuperCollider terminal will reply you with the full path of the folder you need. If it says the folder does not exist, just run `File.mkdir(Platform.userExtensionDir)` or `File.mkdir(Platform.systemExtensionDir)`.
* Navigate your file explorer to this directory, and extract the downloaded SC3Plugins into this folder (the plugins should be in the SC3Plugins folder and not in the directory root).
* Restarting SuperCollider after this is strongy suggested.

## Test your enviroment
* Start your preferred IDE configured as described above / mentioned above
* Create a new file named `test.tidal`
* In the first line of this file, type `setcps 0.4` and press a shift+enter at the end of the line
* You should see the GHCi engine boot up, and a terminal opens up at the bottom of your IDE, prompting something like
```haskell
GHCi, version 8.4.3: http://www.haskell.org/ghc/  :? for help
Prelude> Prelude> Listening for controls on 127.0.0.1:6010
tidal> tidal> 
```
* Start SuperCollider with administrator rights
* Once the help indexing is complete, run the `SuperDirt.start` command. If the SuperDirt boots up successfully, you should see the SuperCollider terminal prompting that `SuperDirt: listening to Tidal on port 57120` after some time it loads the SuperDirt samples.
* If everything seems ok with SuperCollider, go back to your IDE and open up your `test.tidal` file. Go to line 3, and type `d1 $ s "808bd"` and run it with shift+enter.
* This shall play a short bass drum sample slowly. If you here it, you are completely set up!

### Notes for installation
* Google every error message, coming from haskell or SuperCollider. Most of the cases the problem can be resolved by reading the guidelines in your searches.
* Using a boot script for SuperCollider is unadvised at the moment, if you feel experienced enough in SuperCollider and can make it sure that the memory allocation happens after the SuperDirt samples are loaded, just go ahead but note that it can cause malfunction and bad sound quality if you do not understand what is happening in the background.