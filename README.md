### 'mini-bash-lib' is a small source only bash application frame-work

It can be installed as shared source or it can be embedded directly into scripts.
For the shared source installation it supports internationalization (using GNU the
gettext tool).

The library was written to be small and easy to use. It has only 3% of the size of
the larger 'centauri-bash-lib' framework. The packed size is roughly 400 lines and
11 kByte.

### centauri-bash-lib compatibility and coexistence

The 'mini-bash-lib' framework is stand-alone but is compatible with 'centauri-bash-lib'.
In a shared source installation 'mini-bash-lib' is loaded via a small proxy. This proxy
will automatically load 'centauri-bash-lib' if installed and not otherwise disabled.

### Source tree, installation

The sources are organized in a FSH hierarchy structure so that the release tar can be
directly expanded into the **/usr** folder:

        tar --directory=/usr --strip-components=1 --exclude=README.md -xaf <release-tar>

Documentation and examples are at:

        ./share/doc/mini-bash-lib

### Minimal source tree

With internationalization and tools:

        .
        ├── bin
        │   ├── mini10 -> ../src/mini-bash-lib/mini10
        │   ├── _mini_bash_lib -> ../src/mini-bash-lib/_mini_bash_lib
        │   └─ minify -> ../src/mini-bash-lib/minify
        ├── share
        │   ├── doc
        │   │   └── mini-bash-lib
        │   │       ├── default.css             # for html doc
        │   │       ├── default.js              # ...
        │   │       ├── mini-bash-lib.html      # doc as html
        │   │       ├── mini-bash-lib.txt       # doc as text
        │   │       └── README.html             # overview
        │   └── locale                          # localization ...
        │       └── de
        │           └── LC_MESSAGES
        │               ├── mini10.mo
        │               ├── mini-bash-lib.mo
        │               └── minify.mo
        └── src
            └── mini-bash-lib
                ├── mini10                      # l10n tool
                ├── _mini_bash_lib              # proxy
                ├── mini-bash-lib               # library source
                ├── mini-bash-lib.p             # library packed
                └── minify                      # utility

Bare minimum for using shared scripts:

        .
        ├── bin
        │   └── _mini_bash_lib -> ../src/mini-bash-lib/_mini_bash_lib
        └── src
            └── mini-bash-lib
                ├── _mini_bash_lib
                └── mini-bash-lib.p

*End*
