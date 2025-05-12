
Shared and stand-alone use of mini-bash-lib
-------------------------------------------

The library is quite small, so it can be embedded into a script. This was done
for the 'standalone' example, see below. You may copy and edit the 'standalone'
file to your new project or use the 'bin/minify' tool to create one:

        ./bin/minify -W -U -O <file>

The disadvantage of stand-alone scripts are size and updates. To use a newer
library version the embedded library must be replaced. This can be done using
the 'kompare' tool (from 'KDE') or 'bin/minify':

        ./bin/minify -R <file>

A disadvantage of shared scripts is that they will need some sort of installer.
The key concept is the '_mini_bash-lib' proxy that is to be sym-linked either
to '/usr/local/bin' or any folder containing a shared script. The proxy gets 
loaded by the following code:

        PATH+=":${0%/*}" . _mini_bash_lib - '0.01' || exit 2

The proxy has some usefull options, see the 'shared' example for details. If
'centauri-bash-lib' is installed, by default the full library is used. This can
be controlled using the '--mini' command line option.

The '_mini_bash_lib' symlink
----------------------------

For for scripts that load 'mini-bash-lib' via proxy this link is used to load
the proxy unless the proxy installation path is in "$PATH". Example:

        cd ./share/doc/mini-bash-lib/Examples
        ./shared            # loads the demo from the current folder

        cd ..
        Examples/shared     # relative or absolute paths will also work

It is recommended to put a symlink to the proxy into '/usr/local/bin'. Otherwise
every folder containing shared scripts should have this symlink. The folder of
the proxy should also have 'mini-bash-lib' installed or sym-linked. See the 
layout of the release tar as an example.

List of Examples
----------------

    shared              # using mini-bash-lib via proxy
    standalone          # embedding mini-bash-lib, see minify --world

    options             # add custom options to a script
    pipes               # using 'system' with redirections and pipes
    confirm             # demostrates the 'confirm' function
    tester              # run library functions from the command line
    embed               # demonstrates embed, creates doc text and viewer

**End**
