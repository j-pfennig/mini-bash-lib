Files in this folder
--------------------

    _mini_bash_lib          a proxy that either loads mini-bash-lib or centauri-bash-lib
    mini-bash-lib           the library source including documentation and code
    mini-bash-lib.p         packed library code, comments removed. See 'minify' 
    minify                  tool to pack script code or the create a stand-alone template
    mini10                  tool for internationalisation using GNU gettext

The proxy and library options
-----------------------------

For a shared source installation it is recommended to load the library using the provided
proxy. The proxy must not be copied but must be located in the 'mini-bash-lib' source folder.
It should be sym-linked to every folder containing a script that wants to use the shared
source 'mini-bash-lib'. Such scripts then load the proxy using a statement like:

        PATH+=":${0%/*}" . _mini_bash_lib <option>... - <version> || exit 2

The framework includes command line option parsing and thus knows about a few built-in
options in addition to custom options. Some of the built-ins need a proxy option or setting
a variable to be enabled:

    Option      Proxy   Variable        Description
    ------------------------------------------------------------------------------------
    -d --dryrun                         dryrun, make no changes, show what would be done
       --embed                          report a different name, used for script nesting
    -f --force   -f     CEN_FEATURE_F   be less prudent
    -h --help                           help if usage() is implemented
       --mini=0  -n     CEN_FEATURE_N   disable loading of 'centauri-bash-lib'
       --mini=1                         force using 'mini-bash-lib'
    -n --no      -y     CEN_FEATURE_Y   enable --no and --yes options
                 -t     CEN_FEATURE_T   enable internationalization
    -q --quiet                          less output, warnings and errors only
       --trace                          enable bash tracing
    -v --verbose                        verbose output, see trace() 
    -y --yes     -y     CEN_FEATURE_Y   enable --no and --yes options

Packed library code and documentation
-------------------------------------

The 'mini-bash-lib' includes a lot of documentation comments but 'mini-bash-lib.p'
is a packed version with comments and extra spaces removed. The proxy will prefer
the packed version (if newer) but can fall back to the full source.

Documentation comments can be extracted by 'minify' and then be processed be the
'centaurihelp' tool of 'centauri-bash-lib'. Resulting files can be found at:

        ./share/doc/mini-bash-lib

Using minify
------------

Create or update 'mini-bash-lib.p':

        ./minify --empty --uglify --output=. .

Create a shared source hello-world:

        ./minify --world --output=/somwhere/something .

Create a stand-alone hello-world:

        ./minify --world --uglify --output=/somwhere/something .

Notes:

'minify' does not have a real parser for bash syntax. It understands the library
source but probably not much more.

Command-line options:
        --output        output to file (or stdout if option argument is '-')
        --refresh       update a script containing packed library source
        --uglify        packed source, library only, do not use with other code
        --trim          should work with most coding styles
        --world         create a hello-world script

*End*
