Files in this folder
--------------------

    _mini_bash_lib          a proxy that either loads mini-bash-lib or centauri-bash-lib
    mini-bash-lib           the library source including documentation and code
    mini-bash-lib.p         packed library code, comments removed. See 'minify' 
    minify                  tool to pack script code or the create a stand-alone template
    mini10                  tool for internationalisation using GNU gettext

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

        ./minify --mini=1 --empty --uglify --output=. .

Create a stand-alone hello-world:

        ./minify --mini=1 --world --output=/somwhere/something .

Notes:

    'minify' does not have a real parser for bash syntax. It understands the library
    source but probably not much more ...

        --uglify        library only, do  not use with other code
        --trim          should work with most coding styles
    
*End*
