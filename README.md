# Overview

This is a sample code to produce Debian and RPM packages using the
`fpm` tool for testing with the Gemfury service.

# How to use

Easy peasy...

```
bundle
rake
```

# Push packages to Gemfury

This expects you have already set-up the `fury` CLI, and have
pre-authenticated for `push` command.

```
rake push_deb
rake push_rpm
```

# How to contribute

All code / starting point is in the Rakefile.
