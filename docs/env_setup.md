# Chaincode Development Environment

The following is a list of dependencies and recommended tools that you should install in order to develop chaincode.

## Git

- [Git](https://git-scm.com/downloads)
- [Git Desktop](https://desktop.github.com/) (for those uncomfortable with git's CLI)

Git is a great version control tool to familiarize yourself with, both for chaincode development and software development in general. 
Also, git bash, which is installed with git on Windows, is an excellent alternative to the the Windows command prompt. 

### Verify Git Installation

After following the installation instructions above, you can verify that git is installed using the following command:

```
$ git --version
git version 2.11.1.windows.1
```

Once you have git installed, go create an account for yourself on [GitHub](https://github.com/). 
The IBM Blockchain service on Bluemix currently requires that chaincode be in a GitHub repository in order to be deployed through the REST API.

## Go

- [Go download page](https://golang.org/dl)
- [Go installation instructions](https://golang.org/doc/install)
- [Go documentation and tutorials](https://golang.org/doc/)

The Go installation installs a set of Go CLI tools which are very useful when writing chaincode. 
For example, the `go build` command allows you to check that your chaincode actually compiles before you attempt to deploy it to a network. 
At time of writing, this chaincode is known to build successfully with version 1.7.5. 

### Instructions

Follow the installation instructions linked above. 

### Verify Go Installation
You can verify that Go is installed properly by running the following commands. Of course, the output of `go version` may change depending on your operating system.

```
$ go version
go version go1.7.5 windows/amd64

$ echo $GOPATH
C:\gopath
```

Your `GOPATH` does not need to match the one above. 
It only matters that you have this variable set to a valid directory on your filesystem. 
The installation instructions linked above will take you through the setup of this environment variable. 

Next verify you can build GoLang code with the [hello world](https://golang.org/doc/install#testing) example.

## Hyperledger Fabric Releases

- [v1.0.0-preview Hyperledger fabric](https://github.com/hyperledger/fabric/tree/v1.0.0-preview)
- [master branch of the Hyperledger fabric](https://gerrit.hyperledger.org/r/gitweb?p=fabric.git;a=summary)

Any piece of chaincode that you write will need to import the chaincode shim from Hyperledger fabric in order to be able to read and write data to/from the ledger. In order to compile chaincode locally, which you will be doing a lot, you will need to have the fabric code present in your `GOPATH`. Follow the instructions below.

### Fabric Clone Instructions

A few different releases of the fabric are linked above. The release you clone needs to match the Hyperledger network you are using. 
If you are using the Bluemix Blockchain Service, clone the `v1.0.0-preview` branch. 

You will need to make sure that the fabric release you choose is stored under `$GOPATH/src/hyperledger/fabric`. 
The instructions below should take you through the process of properly installing the v0.5 release on your `GOPATH`. 

```

# Create the parent directories on your GOPATH
mkdir -p $GOPATH/src/github.com/hyperledger
cd $GOPATH/src/github.com/hyperledger

# Clone the appropriate release codebase into $GOPATH/src/github.com/hyperledger/fabric
# Note that the v1.0.0-pre release is a branch of the repository.  It is defined after the -b argument
git clone -b v1.0.0-preview https://github.com/hyperledger-archives/fabric.git
```

### Verify Fabric Installation
Open a command prompt/terminal and browse to this directory `$GOPATH/src/github.com/hyperledger/fabric/examples/chaincode/go/chaincode_example02`

```
$ go build .v
```

It should return with no errors/warnings. 

## Node.js

Download the latest Node.js LTS version.

- [Download](https://nodejs.org/en/download/)

Node.js is NOT necessary to develop chaincode, but is to run Marbles.

###  Verify Node.js Installation

Open a command prompt/terminal and make sure the following commands work on your machine:

```
$ node -v
v6.10.1

$ npm -v
3.10.10
```

## IDE Suggestions

### Visual Studio Code

- [Download links](https://code.visualstudio.com/#alt-downloads)

Visual Studio Code is a free IDE that supports both Node.js and Go through plugins.

### Atom

- [Home page](https://atom.io/)

Like VS Code, Atom has plugins to support any of the languages needed to develop chaincode or modify our examples.