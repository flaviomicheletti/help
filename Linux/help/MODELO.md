brewdo(1) -- sandboxing wrapper for brew(1)
====

## SYNOPSIS

`brewdo` <command> [<arguments>...]

## DESCRIPTION

brewdo(1) is a wrapper for brew(1) that sandboxes the installation
process, giving you the following advantages:

-   Your user account loses write rights to `/usr/local`, making
    it much harder to accidentally break your Homebrew-installed
    software (or other `/usr/local` software)

-   Software installations lose write rights to your home directory
    and other places outside `/usr/local`, blocking those installations
    from modifying things they're not supposed to

-   You can cleanly share Homebrew admin rights among multiple users
    of the same system

brewdo uses sudo(1), but not to run commands as `root`; rather, to
run Homebrew under a dedicated sandbox user account.

## QUICK START

Make a backup first!

If you don't have an existing Homebrew installation, `install` can
make one for you:

    sudo brewdo install

If you do have an existing Homebrew installation, `switch` can
migrate it out of your account's ownership and into the brewdo
user's:

    sudo brewdo switch

After either step, you can make brewdo simpler to use by adding an
alias definition to your `.profile`, which makes familiar brew(1)
commands work transparently with brewdo:

    alias brew='brewdo brew'

## COMMANDS

brewdo(1) supports the following primary commands:

*   `brew` <command> [<arguments>]:
    Run brew(1) with the supplied arguments, using sudo(1) to switch to
    the Homebrew user unless <command> is one of a whitelist of commands
    that can be run without switching contexts.

*   `do` <command> [<arguments>...]:
    Use sudo(1) to switch to the Homebrew user and run the supplied
    command.  Intended for maintenance of the Homebrew home.  If the
    sandbox user cannot access the current working directory, brewdo(1)
    will change to `/` first.

*   `install`:
    Create the Homebrew user, log directory, and cache; then clone
    Homebrew into `/usr/local`.  Must be run as `root`.

*   `switch`:
    Create the Homebrew user and log directory, and intelligently
    change ownership on files in the Homebrew home and Homebrew
    cachefrom the current owner (presumably your user account;
    brewdo checks who owns the `.git` directory and cache contents
    to determine this) to the Homebrew user.  `switch` will not
    change ownership on files that do not belong to the user that
    owns the `.git` directory.  Must be run as `root`.

brewdo(1) also supports the following secondary commands, which are
intended for maintenance, step-by-step installation, and uninstallation:

*   `doctor`:
    Perform some checks on the Homebrew setup and report issues.

*   `adduser`:
    Create the Homebrew user.  Normally part of `install` and
    `switch`.  Must be run as `root`.

*   `deluser`:
    Remove the Homebrew user.  This is your final step for cleaning
    up after you've decided you hate brewdo.  Must be run as `root`.

*   `mkdirs`:
    Create the Homebrew log directory, Homebrew home, and the
    Homebrew cache.  Normally part of `install`.  Must be run as
    `root`.

*   `mklogdir`:
    Create the Homebrew log directory.  Normally part of `switch`.
    Must be run as `root`.

*   `clone`:
    Clones Homebrew into the Homebrew home.  Normally part of
    `install`.  Must be run as the Homebrew user.

*   `migrate`:
    Intelligently change ownership on files in the Homebrew home from
    the current owner, as is done as part of `switch`.  Must be run as
    `root`.

*   `unmigrate` <username>:
    Intelligently change ownership on files in the Homebrew home
    from the Homebrew user to the supplied username, and make other
    adjustments.  This would be your first step to returning to a
    stock Homebrew setup from a brewdo setup..  Must be run as
    `root`.

## GLOSSARY

*   Homebrew user:
    The user account that owns the contents of the Homebrew home,
    which brewdo(1) switches to for write operations.  Currently
    `_homebrew`.

*   Homebrew home:
    The directory that stores all Homebrew-installed software and
    Homebrew itself, including its git(1) repository.  In a brewdo(1)
    installation, contents are owned by the Homebrew user; without
    brewdo(1), contents are owned by a regular user.  Currently
    `/usr/local`.

*   Homebrew cache:
    The directory that stores downloaded files and other temporary
    items for Homebrew operation, `/Library/Caches/Homebrew`.

## COMPATIBILITY

brewdo(1) is tested on OS X 10.10 Yosemite and OS X 10.9 Mavericks.

It was once tested on OS X 10.8 Mountain Lion and is expected to still
work there.

## AUTHOR

Matt Behrens <matt@zigg.com>

## SEE ALSO

brew(1), git(1), sudo(8)

[Sandboxing Homebrew](https://www.zigg.com/2014/sandboxing-homebrew.html),
brewdo(1)'s predecessor
