*Nixifying Windows
==================
Are you Linux junky who's suddenly found themselves forced into a Windows environment?
Perhaps your company is making you you use Windows or maybe a less technical friend is having computer troubles.
Either way you've found yourself crushed under the heel of Microsoft's oppressive shell, cmd.exe.
Over the course of this little tutorial we are going to change that.
Rise up my brothers and sisters, you have nothing to lose but your shitty shells.

#Package Management
First myth on the hit parade, windows doesn't have a package manager. 
That's not true.
Well, ok. It doesn't ship with one, but we can add one fairly trivially.
We will use [Chocolatey NuGet](http://chocolatey.org/).
Let's start by popping open the God forsaken piece of software known as cmd.exe.
Run this code:
```
@powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%systemdrive%\chocolatey\bin
```
Dope. Now we have a package manager.
Chocolatey usually installs under the root of the C drive.
We will refer to this directory as %CHOCOLATEY_HOME% from here on out.

#Fixing the Console Window
Next we will fix the Console Window. You can't do a lot of fairly standard things with CMD that you can do with other native window frames.
Like, say, resize the window correctly or copy/paste.
To fix this we'll install [ConsoleZ](https://github.com/cbucher/console). 
ConsoleZ is console window enhancement that is a fork of Console2.
It allows you to do the vast majority of things that you expect from a modern shell window.
Now just to make things a little easier, let's pin ConsoleZ to the Taskbar.
Go to %CHOCOLATEY_HOME%\lib\ConsoleZ.1.9.1.13351\tools and pin the Console.exe to the taskbar.
From here, you can customize ConsoleZ to your liking. There a couple of janky things by default, so you may want to fix those.
I have checked in my configs for references.

#Version Control
Because its not a real computer until it can run Git.
So let's install Git:
```
cinst git
```
Now we have git.
One last bit of pain though. Go into you environment variables and find where Chocolatey added Git\cmd to the Path. 
Change cmd to bin.

#Bash
Because we need a real shell.
So Git for windows ships with Bash. Are you thinking what I'm thinking?
Go into ConsoleZ's settings (ctrl+s) and set the shell to be bash.
It can be found under %GIT_HOME%\bin.
Now restart your shell and you'll being running bash.