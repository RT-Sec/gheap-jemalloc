
# gheap-jemalloc - jemalloc gdb heap plugin

gheap-jemalloc is a jemalloc plugin for gdb

## Usage

Start gdb with the -x flag with the path to the .scm file.

```
> gdb /path/to/binary -x /path/to/repo/gheap-jemalloc.scm
```

Or from gdb itself

```
> gdb binary
(gdb) source /path/to/repo/gheap-jemalloc.scm
```

If you want to load this automatically upon gdb start up, add the
following line to your `.gdbinit` file:

```
source /path/to/repo/gheap-jemalloc.scm
```

where `/path/to/repo` is the path to the cloned git repository


## About

gheap-jemalloc was/is being developed to aid in the debugging of heap
related bugs in applications using jemalloc for linux.

### Reasoning

After searching
the net for appropriate plugins or debuggers for heap related things
I came across quite a few but none of them worked properly. Some
were designed for firefox specifically or for android. `shadow`
for example, is targeted for debugging of jemalloc but somehow it
simply doesnt work with jemalloc 5.3.0 from my experience.

### Goals

The goal of this project is to provide a consitent interface to
inspecting, testing and debugging of the heap for applications
using the _linux jemalloc standalone_ binary.

### Versions

There are quite a few versions of jemalloc so this project provides
a gdb plugin for the standalone version of jemalloc for linux, version
5.3.0 (and up, hopefuly)

## Features

Current features are limited and only provide some basic commands, such
as `jeslabs` and `je_narenas_total` and `je_nbins_total` which show the slabs, number
of arenas and number of bins respectivelly.

### Programming language

`guile` was chosen for this module, because it is a `scheme` programming
language and because most python scripts and plugins are terrible, unreliable and slow.
This wont change so don't even ask. Python related pull-request will be rejected.

As an added bonus, guile is GNU software, so I think it fits better into the _Free Software_
ecosystem than `python` which is MIT licensed.

## Requests, suggestions and features

gheap-jemalloc provides mostly just basic features for inspecting the heap.
In case you'd like support to be added for other jemalloc versions, open
an issue of the format

`[Linux standalone] Version request for jemalloc X.Y.Z`

Where X.Y.Z is the version you'd like supported. and `Linux standalone` is
the OS flavor. Right now though, only the linux standalone versions are considered.
But Windows, FreeBSD and MacOS support might be added in the future.

# License

This software is licensed under the GNU GPL version 3+ license. See COPYING
for more information.