---
title: "Creating a Barebones Golang Project with Vendoring Via a Custom Setup Script"
date: 2018-06-09T16:21:53-04:00
draft: false

featuredImage: "/images/boxes.jpg"
categories: ["software", "golang", "bash", "setup scripts"]
tags: ["software", "golang", "bash", "setup scripts"]
author: "Nisarga Patel"
twitter:
  card: "summary"
  site: "@nphacker"
  title: "Creating a Barebones Golang Project with Vendoring Via a Custom Setup Script"
  description: "I recently created a simple script which allows one to quickly scaffold a Go project, here's how to use it."
  image: "https://nisarga.io/images/boxes.jpg"
---

Often times one may want to create a barebones Go project with dependency vendoring. I recently created a simple script which allows one to quickly scaffold a Go project that uses the vendoring tool [govendor](https://github.com/kardianos/govendor).

##### Prerequisites

In order to use the script you must have already installed Go, if you're on Mac and have [Homebrew](https://brew.sh). You can easily install Go via `brew install go`. For install directions for other platforms check out [the official Go docs](https://golang.org/doc/install). This tutorial is written from the perspective of Mac or Linux.

##### The barebones project setup script

The project setup script scaffolds out project folders and prompts you to add common dependencies and also has support for adding your own custom dependencies. 

You can take a look at the code for the setup shell script [here](https://github.com/WLMS/project-starter-scripts/blob/master/setup-go-project.sh).

##### How to use it

After you have installed Go, the first step is to get the code for the script via `git clone`:

```bash
git clone https://github.com/WLMS/project-starter-scripts.git
```

Elsewhere create a new directory for your project

```bash
mkdir projectname
```

Copy over the starter script from the cloned directory into your project directory

```bash
cp project-starter-scripts/setup-go-project.sh projectname/
```

Change directories to the project directory

```bash
cd projectname/
```

Run the script

```bash
./setup-go-project.sh
```

Upon running the script you will be prompted for the name of your username or organization, and the name of your project.

Here is an example:

```text
Welcome to the Golang project starter
Enter the GitHub organization or username: YOURUSERNAME
Enter the name of your project repo: YOURPROJECTNAME
Setting up directories...
Brought in govender and installed dependencies via ...
Common dependencies...
Do you want gin-gonic? (y/n):
```

Next you will be prompted if you'd like certain common dependencies in your project

```text
Do you want gin-gonic? (y/n): n
Do you want mgo (mongo driver)? (y/n): n
Do you want pq (postgres driver)? (y/n): n
Do you want mysql (mysql driver)? (y/n): n
Do you want gocql (apache cassandra driver)? (y/n): n
Do you want go-redis (redis driver)? (y/n): n
Do you want gin-jwt? (y/n): n
Do you want jwt-go? (y/n): n
Do you want protoc-gen-go (protocol buffers for gRPC)? (y/n): y
Do you want any custom dependencies? (y/n): y
Whats the url for your custom dep: github.com/uber-go/zap
Do you want any custom dependencies? (y/n): n
Run source setenv.sh to set your GOPATH and GOBIN.
```

At the end you'll be prompted for any custom dependencies which you can specify. It will keep on prompting you for custom dependencies until you type `n`.

At this point your barebones Go project should be all setup for development. In order for your files to notice the dependencies you have to specify the GOPATH and GOBIN environment variables. The setup script creates a `setenv.sh` file which does this for you if you run `source setenv.sh`, you can also optionally create an alias in your bash configuration that sets those path variables.

You can look at the value of your GOPATH and GOBIN variables by running:

```
echo $GOBIN && echo $GOPATH
```

##### Creating a Go file and testing out a dependency

After ensuring that your GOPATH and GOBIN variables are set to your root project directory you can now test out a dependency by creating a Go file.

In your project directory

```
cd src/github.com/YOURUSERNAME/YOURPROJECTNAME
```

And create a file called `main.go`. Here is a sample Go file that uses the custom `zap` logger dependency added:


```Go
package main

import (
	"go.uber.org/zap"
	"time"
)

func main() {
	logger, _ := zap.NewProduction()
	defer logger.Sync()
	logger.Info("Testing the logger",
		zap.String("Some String", "An important string"),
		zap.Int("Some Integer", 5),
		zap.Duration("Some Duration", time.Second),
	)
}
```

As long as your GOPATH and GOBIN variables are set correctly to the project root running `go run main.go` should give you the following output:

```bash
> go run main.go
{"level":"info","ts":1528577748.722416,"caller":"YOURPROJECTNAME/main.go:11","msg":"Testing the logger","Some String":"An important string","Some Integer":5,"Some Duration":1}
```

##### Setting GOPATH and GOBIN via a bash alias

Here's the alias for quickly setting the GOPATH and GOBIN environment variable if you choose not to use the `source setenv.sh` method:

```
alias gp='GOPATH=`pwd`; export GOPATH; GOBIN=$GOPATH/bin; export GOBIN'
```

Usually you can add the alias in the `~/.bashrc` or `~/.bash_profile` file, you can find out what the bash configuration file is for your particular OS. 

#### Expansions

I often create a Makefile as well for larger projects which has support for cross platform compilation:

```Makefile
all_linux: 
	GOOS=linux GOARCH=amd64 go build -o bin/programname-linux-amd64 src/github.com/YOURUSERNAME/YOURPROJECTNAME/*.go
all_mac_os: 
	cp config.json bin/config.json
	GOOS=darwin GOARCH=amd64 go build -o bin/programname-mac-os-amd64 src/github.com/YOURUSERNAME/YOURPROJECTNAME/*.go 
all_arm: 
	cp config.json bin/config.json
	GOOS=linux GOARCH=arm go build -o bin/programname-linux-arm src/github.com/YOURUSERNAME/YOURPROJECTNAME/*.go 
clean:
	rm -r bin/*
```

Using this Makefile it becomes easy to compile for different platforms by doing:

```
make all_linux
or
make all_mac_os
or 
make all_arm
```

I would also have a Makefile command for running tests as well.

##### Conclusion

I hope you enjoyed this post on setting up a barebones Go project with vendoring via a setup script. If you have any suggestions, edits, or comments feel free to comment down below.

Thanks!