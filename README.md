roveralls
=========

A Go recursive coverage testing tool.

[![GoDoc](https://godoc.org/github.com/lawrencewoodman/roveralls?status.svg)](https://godoc.org/github.com/lawrencewoodman/roveralls)
[![Build Status](https://travis-ci.org/lawrencewoodman/roveralls.svg?branch=master)](https://travis-ci.org/lawrencewoodman/roveralls)
[![Build status](https://ci.appveyor.com/api/projects/status/5dcyd6wgu7fxt538?svg=true)](https://ci.appveyor.com/project/lawrencewoodman/roveralls)
[![Coverage Status](https://coveralls.io/repos/lawrencewoodman/roveralls/badge.svg?branch=master)](https://coveralls.io/r/lawrencewoodman/roveralls?branch=master)
[![Go Report Card](https://goreportcard.com/badge/github.com/lawrencewoodman/roveralls)](https://goreportcard.com/report/github.com/lawrencewoodman/roveralls)


roveralls runs coverage tests on a package and all its sub-packages.  The coverage profile is output as a single file called 'roveralls.coverprofile' for use by tools such as goveralls.

This tool was inspired by [github.com/go-playground/overalls](https://github.com/go-playground/overalls) written by Dean Karn, but I found it difficult to test and brittle so I decided to rewrite it from scratch.  Thanks for the inspiration Dean.

Usage
-----
At its simplest, to test the current package and sub-packages and create a `roveralls.coverprofile` file in the directory that you run the command:

    $ roveralls

To see the help for the command:

    $ roveralls -help

        roveralls runs coverage tests on a package and all its sub-packages.  The
        coverage profile is output as a single file called 'roveralls.coverprofile'
        for use by tools such as goveralls.

        Usage of roveralls:
          -covermode count,set,atomic
              Mode to run when testing files: count,set,atomic (default "count")
          -help
              Display this help
          -ignore dir1,dir2,...
              Comma separated list of directory names to ignore: dir1,dir2,... (default ".git,vendor")
          -short
              Tell long-running tests to shorten their run time
          -v	Verbose output


View Output in a Web Browser
----------------------------
To view the code coverage for you packge in a browser:

    $ go tool cover -html=roveralls.coverprofile

Use with goveralls
------------------
 The output of `roveralls` is the same as the the standard `go test -coverprofile=profile.coverprofile` but with multiple files tested in the output file.  This can therefore be used with tools such as `goveralls`.

If you wanted to call it from a `.travis.yml` script you could use:

    - $HOME/gopath/bin/roveralls
    - $HOME/gopath/bin/goveralls -coverprofile=roveralls.coverprofile -service=travis-ci

Contributing
------------

If you want to improve this program make a pull request to the [repo](https://github.com/lawrencewoodman/roveralls) on github.  Please put any pull requests in a separate branch to ease integration and add a test to prove that it works.  If you find a bug, please report it at the project's [issues tracker](https://github.com/lawrencewoodman/roveralls/issues) also on github.


Licence
-------
Copyright (C) 2016, mmsqep

This software is licensed under an MIT Licence.  Please see the file, LICENCE.md, for details.
