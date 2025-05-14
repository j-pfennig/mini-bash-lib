**'mini-bash-lib' is a small source only bash application frame-work**

It can be installed as shared source or it can be embeded directly into scripts.
For the shared source installation it supports internationalisation (using GNU the
gettext tool).

The library was written to be small and easy to use. It has only 1% of the size of
the larger 'centauri-bash-lib' framework. The packed size is roughly 400 lines and
11 kByte.

**centauri-bash-lib compatibility and coexistence**

The 'mini-bash-lib' framework is stand-alone but is compatible with 'centauri-bash-lib'.
In a shared source installation 'mini-bash-lib' is loaded via a small proxy. This proxy
will automatically load 'centauri-bash-lib' if installed and not otherwise disabled.

**Source tree, installation**

The sources are organized in a FSH hierarchy structure so that the release tar can be
directly expanded into the **/usr** folder:

        tar --directory=/usr --strip-components=1 -xaf <release-tar>

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