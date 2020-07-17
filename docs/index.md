# binq

[binq](https://github.com/binqry/binq) is a light-weight software installer written in Golang.  
It downloads stuff querying an HTTP URL and extracts them if they are compressed.  
Especially, **binq** makes it easy to get stuff which is not provided by any package manager but has
a download URL.

## Contents

The documentation contains followings:

- [Installation Guide](#installation) for **binq** binary
- [Quickstart](./quickstart/) to get Items by **binq** command
- [More Usages](./cli-usage/) of **binq** command
- [Terminology](./terminology/)

## System Requirements

Pre-built binaries are available for macOS and Linux with x86-64 CPU architecture.

**binq** is logically supposed to work on any machine for which Go can compile codes.

Known issues:

- Installation process on Windows may not work.

## Installation

Choose one of below methods:

- [Homebrew](https://brew.sh/) or [Linuxbrew](https://docs.brew.sh/Homebrew-on-Linux) (using Tap)
- Download from GitHub releases
- go get (go command is required)

Description for each method follows.

### Homebrew (Linuxbrew)

```sh
brew tap progrhyme/taps
brew install binq
```

### Download Pre-built Binary

The following script detects your OS and downloads the latest binq binary into your current directory:

```sh
curl -s "https://raw.githubusercontent.com/binqry/binq/master/get-binq.sh" | bash
```

Other versions are available on [GitHub Releases](https://github.com/binqry/binq/releases).

### go get

Just run this:

```sh
go get github.com/binqry/binq/cmd/binq
```

## License

The MIT License.

Copyright &copy; 2020 IKEDA Kiyoshi
