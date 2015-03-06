# vcs-lint

perform some lint-like checks against repositories, with an emphasis on Debian
packaging repositories. Things it checks for include:

 * local branches which are not present on the 'origin' remote
 * commits to local branches which have not been pushed to their origin equivalents

Debian packaging specific:

 * missing git tags corresponding to package versions

I originally wrote this intending it to be used with Joey Hess's
[mr](https://joeyh.name/code/mr/) ("my repos") tool.

## Example

    $ mr-lint wd/debian/bup
    wd/debian/bup: local branches not present in origin: rescue-diverge
    wd/debian/bup: local branch debian does not match origin branch debian
    wd/debian/bup: local branch master does not match origin branch master
    wd/debian/bup: 5 missing upstream tags: 0.21, 0.17b, 0.20, 0.24b, 0.14a
    wd/debian/bup: 3 missing debian tags: debian/0.17b-1, debian/0.20-2, debian/0.21-1

## using with `mr`

From memory, I think you add something like this to the `[DEFAULT]` section of your `~/.mrconfig`:

    lint = vcs-lint
    
(adjust path to `vcs-lint` as appropriate.)
