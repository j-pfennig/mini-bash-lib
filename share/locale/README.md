**internationalisation support**

The 'mini10' script uses the GNU 'gettext-tools' to build the data structure and
message catalogues for internationalization (i10n). This looks like the following:

        <locale>/<lang>/<translations>              # editable translation source
        <locale>/<lang>/LC_MESSAGES/<catalogue>     # distributable binaries

Example (have a look at 'mini10.po'):

        locale/de/mini10.po                         # german translation source
        locale/de/LC_MESSAGES/mini10.mo             # run-time loadable

Obviously this supports multiple languages (see LANG environment variable). Only
the directory structure and '.mo' files must be present at run-time, the '.po'
files do not need to be distributed.

**how it works**

By default 'mini-bash-lib' does i10n when using the '_mini_bash_lib' proxy
with option -t. Technically this means setting two bash specific variables:

1. set TEXTDOMAINDIR to the 'locale' folder
2. set TEXTDOMAIN to the 'catalogue' name (e.g. the script name)

Bash then translates all $"" string literals at load time depending on current
locale settings. To explicitly disable i10n use the 'C' locale:

        LANG=C <tool> <args>...


**edit source and update translation source (.po)**

To internationalize the 'myscript' example use something like the following workflow:

    cd      src/scripts                 # location for scripts 
    editor  myscript                    # use dollar signs to flag translations
    chmod   775 myscript                # make it executable
    ln -s   myscript ../../bin          # make script public

    cd      ../../share/locale          # i10n folder
    ln -s   ../../src/script/myscript   # making a symlink is recommended
    mini10  lang fr                     # 1st time onla, create frensh
    mini10  dump myscript 

**edit translations and build binary (.mo)**

    editor              locale/de/mini-bash-lib.po
    locale/l10n-tool    build   mini-bash-lib  --out=locale/de 
