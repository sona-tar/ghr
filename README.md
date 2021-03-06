ghr [![wercker status](https://app.wercker.com/status/a181c474f1e25e1870d0ba387723046b/s "wercker status")](https://app.wercker.com/project/bykey/a181c474f1e25e1870d0ba387723046b) [![Coverage Status](https://coveralls.io/repos/tcnksm/ghr/badge.png?branch=master)](https://coveralls.io/r/tcnksm/ghr?branch=master) [![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](https://github.com/tcnksm/ghr/blob/master/LICENCE)
====

Easily ship your project to your user using Github Releases

## Description

`ghr` enable you to create Release on Github and upload your artifacts to it. `ghr` will parallelize upload multiple artifacts.

## Demo

![](http://deeeet.com/writing/images/post/ghr.gif)

Result is [here](https://github.com/tcnksm/ghr/releases/tag/v0.1.0).


## Usage

Run it in your project directory:

```bash
$ ghr [option] <tag> <artifacts>
```

You need to set `GITHUB_TOKEN` environmental variable:

```bash
$ export GITHUB_TOKEN="....."
```

## Example

To upload all package in `pkg` directory with tag `v0.1.0`

```bash
$ ghr v0.1.0 pkg/
--> Uploading: pkg/0.1.0_SHASUMS
--> Uploading: pkg/ghr_0.1.0_darwin_386.zip
--> Uploading: pkg/ghr_0.1.0_darwin_amd64.zip
--> Uploading: pkg/ghr_0.1.0_linux_386.zip
--> Uploading: pkg/ghr_0.1.0_linux_amd64.zip
--> Uploading: pkg/ghr_0.1.0_windows_386.zip
--> Uploading: pkg/ghr_0.1.0_windows_amd64.zip
```

Or if you want to replace artifact which is already uploaded:

```bash
$ ghr --replace v0.1.0 pkg/
```

## Options

You can set some options:

```bash
$ ghr \
    -t <token> \       # Set Github API Token
    -u <username> \    # Set Github username
    -r <repository> \  # Set repository name
    -p <num> \         # Set amount of parallelism (Default is number of CPU)
    --replace \        # Replace asset if target is already exists
    --delete \         # Delete release in advance if it exists
    --draft \          # Release as draft (Unpublish)
    --prerelease \     # Crate prerelease
    <tag> <artifacts>
```

## Install

If you are OSX user, you can use [Homebrew](http://brew.sh/):

```bash
$ brew tap tcnksm/ghr
$ brew install ghr
```

If you are in another platform, you can download binary from [relase page](https://github.com/tcnksm/ghr/releases) and place it in `$PATH` directory.

## Integration with CI-as-a-Service

You can integrate ghr with CI-as-a-Service to release your artifacts after test passed. It's very easy to provide latest build to your user continuously.

See [Integrate ghr with CI as a Service](https://github.com/tcnksm/ghr/wiki/Integrate-ghr-with-CI-as-a-Service) page.

## VS.

- [aktau/github-release](https://github.com/aktau/github-release) - `github-release` can also create and edit releases and upload artifacts. It has many options. `ghr` is a simple alternative. And `ghr` will parallelize upload artifacts.

## Contribution

1. Fork ([https://github.com/tcnksm/ghr/fork](https://github.com/tcnksm/ghr/fork))
1. Create a feature branch
1. Commit your changes
1. Rebase your local changes against the master branch
1. Run test suite with the `make test` command and confirm that it passes
1. Run `gofmt -s`
1. Create new Pull Request

You can get source with `go get`:

```bash
$ go get -d github.com/tcnksm/ghr
$ cd $GOPATH/src/github.com/tcnksm/cli-init
$ make install
```

## Support

If you have something to ask me or request for new features, feel free to join gitter room.

[![Gitter](https://badges.gitter.im/Join Chat.svg)](https://gitter.im/tcnksm/ghr?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)


## Author

[tcnksm](https://github.com/tcnksm)
