# Live Coding School
## March 3-8. 2020, Budapest

This is the public repository for the workshop material of the event regarding Tidal Cycles.

## Installing Tidal Cycles
## ...with avoiding dead ends

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