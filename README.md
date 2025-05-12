**'mini-bash-lib' is a small source only bash application frame-work**

It can be installed as shared source or it can be embed directly into scripts.
For the shared installation it supports internationalisation (GNU gettext).

It was written to be small and easy to use. It has only 1% of the size of the
larger 'centauri-bash-lib' framework. 

**centauri-bash-lib compatibility and coexistence**

The 'mini-bash-lib' framework is stand-alone but is compatible with 'centauri-bash-lib'.
The shared installation will automatically load 'centauri-bash-lib' if installed.

**Source tree, installation**

The sources are organised in a FSH hierarcy structure so that the release tar can be
directly expanded from the **/usr** folder:

        cd /usr
        tar -xaf <release-tar>

Documentation and examples are at:

        ./share/doc/mini-bash-lib

**Minimal source tree**

With internationalization and tools:

        .
        ├── bin
        │   ├── mini10 -> ../src/mini-bash-lib/mini10
        │   ├── _mini_bash_lib -> ../src/mini-bash-lib/_mini_bash_lib
        │   └─ minify -> ../src/mini-bash-lib/minify
        ├── share
        │   ├── doc
        │   │   └── mini-bash-lib
        │   │       ├── default.css
        │   │       ├── default.js
        │   │       ├── mini-bash-lib.html
        │   │       └── mini-bash-lib.txt
        │   └── locale
        │       └── de
        │           └── LC_MESSAGES
        │               ├── mini10.mo
        │               ├── mini-bash-lib.mo
        │               └── minify.mo
        └── src
            └── mini-bash-lib
                ├── mini10
                ├── _mini_bash_lib
                ├── mini-bash-lib
                ├── mini-bash-lib.p
                └── minify
  
Bare minimum for using shared scripts:

        .
        ├── bin
        │   └── _mini_bash_lib -> ../src/mini-bash-lib/_mini_bash_lib
        └── src
            └── mini-bash-lib
                ├── _mini_bash_lib
                └── mini-bash-lib.p

*End*