---
layout: post
title: Setup Python Protocol Buffer Mac OS
categories: Python
tags: Protocol Buffer, Python, Mac OS
comments: true
---

![Protocol Buffer](/public/images/protocol-buffers/protocolbuffers.png)

## Protocol Buffer

Protocol buffers are a flexible, efficient and automated mechanism for serializing structured data.
They are like XML but much simpler, faster and smaller. We define the structure and then generate
source code to easily write and read from a variety of data sources.

### Dependencies to build Protocol Buffer

The following dependencies are required to successfully build and install Protocol Buffers.

```bash
$ brew install libtool autoconf automake
```

### Building Protocol Buffer: Python

* Download the appropriate python release here: https://github.com/google/protobuf/releases
* Unzip the folder
* Enter the folder and run 
```bash
$ ./autogen.sh
$ ./configure
$ make -j4
```

**Note:** The -j[n] tells the `make` command to use multiple jobs in the build process. You can change `n` depending on your 
system.

### Verify and install

After the build completes, verify and install Protocol Buffers using the below commands.

```bash
$ make -j4 check
$ sudo make install
```

### Check your installation
Ocne the installation is successful, check the version and path to validate the installation.

```bash
$ which protoc
$ protoc --version
```

### Next step

Go through the [Protocol Buffer Basics: Python](https://developers.google.com/protocol-buffers/docs/pythontutorial) tutorial from google.


