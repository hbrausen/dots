# dots
Dotfiles in a GNU Stow-able format

[Alternative guide](https://linuxconfig.org/how-to-use-gnu-stow-to-manage-programs-installed-from-source-and-dotfiles)

# Managing installed-from-source packages using GNU stow

One issue, traditionally, with installing a bunch of software from source into a prefix (such as `$HOME/local` or `/usr/local`) is that you end up with a bunch of loose files spread all over your install prefix, which can make uninstalling/updating software a headache.

[GNU Stow](https://www.gnu.org/software/stow/manual/stow.html) helps fix this ugliness by using symlinks.

Let's say I have `$HOME/local/bin` in my path. Instead of installing a package called "packagename" to a prefix of `$HOME/local`, install it to `$HOME/local/stow/packagename`. Then you'll end up with `$HOME/local/stow/packagename/bin` `$HOME/local/stow/packagename/include`, .etc.

Then, `cd` into `$HOME/local/stow` and run `stow packagename`. This links all the files in `$HOME/local/stow/packagename/` to `$HOME/local/`, thus "installing" the package.

To remove the package, simply run `stow -D packagename` from the stow directory.

# Managing dotfiles

Many devs like to store their dotfiles in source control. You can use stow to symlink source controlled dotfiles back into your home directory, `~/.config/`, etc.

An advantage of using stow is that you can bundle config files together for a given app, even if those config files are normally scattered throughout your home directory.

# Installing the configuration for an application

For example, installing all configuration files for `vim`:

```
$ cd dots
$ stow vim
```

# Uninstalling the configuration for an application

Uninstalling the custom configuration for `vim`:

```
$ cd dots
$ stow -D vim
```

