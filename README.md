# Firewatch

Is your user-base complaining their environment(s) broke after running `conda update [your_package]`? I bet they are! Have you ever wondered what packages were introduced into the Conda ecosystem without your knowledge? Wonder no more!

## License

BSD 3-clause

## Support

- None.
- Use at your own risk.

## Requirements

This utility requires Python 3.6 or greater and `requests`.

## Usage

```
usage: firewatch [-h] [--benchmark] [--brute-force] [--channel CHANNELS] [--deprecated] [--order ORDER]
                 [--platform PLATFORMS] [--r-lang] [--time-span TIME_SPAN] [--version]
                 [package ...]

positional arguments:
  package               Return package starting with pattern PACKAGE

options:
  -h, --help            show this help message and exit
  --benchmark           Display total time to parse and sort channel data
  --brute-force         Derive timestamps from HTTP header: "last-modified"
  --channel CHANNELS, -c CHANNELS
                        Conda channel
  --deprecated, -d      Enable deprecated Anaconda, Inc. channel(s)
  --order ORDER, -o ORDER
                        [asc|dsc]
  --platform PLATFORMS, -p PLATFORMS
                        [linux|osx|win]-[32|64]
  --r-lang, -R          Enable R channels
  --time-span TIME_SPAN, -t TIME_SPAN
                        i[s|m|h|d|w|M|y|D|c] (120s, 12h, 1d, 2w, 3m, 4y)
  --version, -V         Display software version
```


## Examples

_What's probably broken within..._

... the last 24 hours?

```bash
$ firewatch -t 1d
```

... the last week?

```bash
$ firewatch -t 1w
```

... three days on some high profile anaconda.org channels?

```bash
$ firewatch -t 3d -c conda-forge -c intel
```

... the last month on AstroConda?

```bash
$ firewatch -t 1M -c http://ssb.stsci.edu/astroconda
```

_What about showing only certain packages?_

You are in luck. Issue package name(s) as positional arguments.

```
$ firewatch -c conda-forge cfitsio hstcal
```
