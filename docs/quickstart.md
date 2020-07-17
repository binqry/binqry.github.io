# Quickstart

This page illustrates how to get stuff by **binq** command.  
We call them [**Items**](../terminology/#item) which are installed by binq.

## Command Syntax

```sh
binq [install] [-t|--target] SOURCE[@VERSION] \
  [-d|--dir OUTPUT_DIR] [-f|--file OUTFILE] \
  [-s|--server SERVER] \
  [-z|--no-extract] [-X|--no-exec] \
  [-L|--log-level LOG_LEVEL]
```

## Install "Items"
### Basics

First of all, you can specify full download URL for an item as `SOURCE` argument.

```sh
binq https://github.com/peco/peco/releases/download/v0.5.7/peco_darwin_amd64.zip \
  -d path/to/bin

export BINQ_BIN_DIR=path/to/bin
binq https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 \
  -f jq
```

The default destination is current directory.  
It will be overridden by environment variable `BINQ_BIN_DIR` or command-line option `-d|--dir`.

By default, **binq** finds executable files in archive and place them to destination.  
Therefore, binq can be a handy shortcut of `curl` and `unzip` (or `tar xf` or whatever).

### With "Index Server"

[**Index Server**](../terminology/#index-server) of binq is an HTTP server which serves information
of _items_.  
With _index server_, you can install _items_ in more convenient and safer way.

The default _index server_ [https://binqry.github.io/index](https://binqry.github.io/index) holds
data of some famous software.

You can get them by following commands:

```sh
binq mdbook
binq jq@1.6 # installed as `jq`
```

Because the [item manifest](../terminology/#item-manifest) of "jq" contains the output file name of
"jq" binary, you don't need to specify `-f|--file OUTFILE` option in this case.  
Compare this behavior to previous example with direct download URL.
