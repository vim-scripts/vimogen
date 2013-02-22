
Vimogen is perhaps the easiest way to install, remove, or update Vim plugins.

Requiring zero-configuration, vimogen is essentially a Pathogen bundle manager
that manages the installing/deleting/updating of all your Vim plugins. It also
makes it easy to keep all of your Vim plugins synchronized across different
machines.

Simply create a manifest file in your home directory called .vimogen_repos 
(or let vimogen generate one for you) and put git URLs to Vim plugins in 
it, one line at a time, like:
    
    git://github.com/tpope/vim-surround.git
    git://github.com/tpope/vim-rails.git
    git://github.com/scrooloose/nerdtree.git
    git://github.com/godlygeek/tabular.git
    ...

Running vimogen will give you the option to install, update, or uninstall
the Vim plugins you use. 

FAQ
===
Q: What is pathogen?

A: Pathogen has become the de-facto standard way of activating Vim plugins
that were installed in modular way into their own directories, rather than
simply unzip'ing all plugins into the same directory like old times.
Vimogen assumes you're using Pathogen. So install Pathogen first, which is
as easy as following the simple steps on https://github.com/tpope/vim-pathogen

Q: Where can I find git URLs for Vim plugins?

A: All of the plugins from vim.org are mirrored on https://github.com/vim-scripts

Q: I downloaded a Vim plugin as a .zip file. What should I do?

A: Delete it. Vimogen doesn't use zip files, it uses git repositories. All of
the plugins from vim.org are mirrored on https://github.com/vim-scripts so
find it on there and put the remote repository URL into ~/.pathogen_repos.

Q: What does zero-configuration mean?

A: I mean it in the sense of not having to modify your vimrc file at all in
order to use Vimogen. To be fair, if you don't already have Pathogen installed
then adding a one line configuration that it requires to your vimrc is still
necessary. Also, if ~/bin isn't in your system $PATH yet you'll need to add it
in your bashrc, or equivalent, but that is more of an optional installation step.

Q: Is Vimogen really the easiest way to manage Vim plugins?

A: I think so. I evolved the way I was handling it into this script. There
are other ways to handle the automation of installing Vim plugins via 
pathogen -- such as making your entire .vim directory a git repo and then
making the plugin directories git submodules. There are also other plugin
managers such as Vundle. I find Vimogen to be the easiest method I've seen. 

Requirements
============
A Unix-like system (Linux, OS X, etc.) running the Bash shell.

Vim and the [Pathogen](https://github.com/tpope/vim-pathogen/ "Pathogen") plugin.

Git.

So it will not work if you use Windows or Zsh, for example. Feel free to fork it
and make it work on Windows or other shells besides bash if you want to, though!

Installation
============
Installation is optional.

Create a manifest file called $HOME/.vimogen_repos that consists
of just git repositories. I supplied a ample .vimogen_repos file
which contains the plugins that I like to use; make up your own, though.

Note that Vimogen wil auto-enerate $HOME/.vimogen_repos if you run it
without creating the file first. It will genereate it based off the
current pathogen bundles you already have, if any.

Then:

    git clone git://github.com/rkulla/vimogen.git
    chmod u+x vimogen.sh
    cp vimogen.sh ~/bin/vimogen 
    
or put it somewhere else in your $PATH if you don't like ~/bin.

Usage
=====
Run vimogen without arguments:

    $ vimogen

It will give you a menu of items to choose from:

    1) Install
    2) Uninstall
    3) Update
    4) Exit
    Select a menu option to perform: 1

*    If you choose __Install__, then it will a _git clone_ on all the git repositories 
that you specified in ~/.vimogen_repos into your Pathogen dir (~/.vim/bundle).
It will skip any directories that already exist. You can also append new plugin
repos to the .vimogen_repos file later and install them incrementally by re-
running Vimogen's install command.

*    If you choose __Uninstall__, it will give you a list of all your plugins to choose from:

         1) EXIT                  8) tabular             15) vim-matchit
         2) ctrlp                 9) taglist             16) vim-rails
         3) dbext                10) tComment            17) vim-repeat
         4) nerdtree             11) tlib_vim            18) vim-snipmate
         5) pydiction            12) vcscommand          19) vim-surround
         6) python-mode          13) vim-addon-mw-utils  20) ZenCoding
         7) snipmate-snippets    14) vim-jade
         Select a plugin to completely uninstall:

    
*    If you choose __Update__, then it will run a _git pull_ on all of your bundles. 
This is great because you can stay up-to-date with all the new features the 
plugin authors create just by re-running this command often.

License
=======
Copyright (c) Ryan Kulla. Distributed under the same terms as Vim itself. See :help license
