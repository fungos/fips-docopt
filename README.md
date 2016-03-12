fips-docopt
===========

[![Build Status](https://travis-ci.org/fungos/fips-docopt.svg)](https://travis-ci.org/fungos/fips-docopt)

fipsified [docopt.cpp](https://github.com/docopt/docopt.cpp)

more on fips build system: https://github.com/floooh/fips

To use docopt.cpp you need just to add it to your `fips.yml`:

```cmake
imports:
     fips-docopt:
         git: https://github.com/fungos/fips-docopt.git
```

NOTE: docopt.cpp requires exception support to be enabled (FIPS_EXCEPTIONS).
