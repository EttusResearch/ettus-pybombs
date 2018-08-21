# Ettus Research PyBOMBS Recipes

## List of recipes

| Name                    | Type   | Description
|-------------------------|--------|--------------------------------------------------------------------------
| rfnoc                   | prefix | Native RFNoC configuration, includes gr-ettus (e.g. for X310 dev)
| e3xx-default            | prefix | E310 cross-compile environment with default UHD (as shipped on SD card)
| e3xx-custom-uhd         | prefix | E310 cross-compile environment with latest UHD (master branch)
| e3xx-latest-maint       | prefix | E310 cross-compile environment with latest UHD (maint branch)
| e3xx-rfnoc              | prefix | E310 cross-compile environment with RFNoC enabled, includes gr-ettus
| uhd-e310-release4-host  | prefix | Host-side environment to use a release 4 E310 in network mode
| e3xx-release4-sdk       | sdk    | E310 release 4 SDK

## Prerequisites

To use these recipes, you need PyBOMBS installed and initialize this recipe
repository. You also need at least the gr-recipes repository enabled.

To install the latest official release of PyBOMBS, simply run

    $ [sudo] pip install PyBOMBS

However, you might want to run the latest bleeding edge version of PyBOMBS,
which you can install by running

    $ [sudo] pip install [--upgrade] git+https://github.com/gnuradio/pybombs.git

After initialization, make sure you have the gr-recipes and ettus-pybombs
repositories enabled:

    $ pybombs recipes add gr-recipes git+https://github.com/gnuradio/gr-recipes.git
    $ pybombs recipes add ettus-pybombs git+https://github.com/EttusResearch/ettus-pybombs.git

See the PyBOMBS manual for more details:
- https://github.com/gnuradio/pybombs/blob/master/README.md

## Using these recipes

There are different types of recipes:

- Package recipes
- Prefix recipes
- SDK recipes

Usage depends on the type of recipes. SDK recipes attach an SDK to a prefix,
and are usually referenced when initializing a prefix:

    $ pybombs prefix init --sdk <name> -a <alias> <path>

Prefix recipes initialize a prefix with a full set of configuration options
and packages, e.g.:

    $ pybombs prefix init -R <recipe> -a <alias> <path>

This can include SDKs, and may take a while. Example:

    $ pybombs prefix init -R e3xx-custom-uhd ~/prefix/e300

...will create a directory in `~/prefix/e300`, install the E300 SDK, and install
a version of UHD from source. This will let you test latest UHD on an E310 with
the minimum of effort.

