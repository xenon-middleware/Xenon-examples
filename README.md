[![Build Status](https://travis-ci.org/NLeSC/Xenon-examples.svg)](https://travis-ci.org/NLeSC/Xenon-examples)

This repository contains the source of the [Xenon](https://nlesc.github.io/Xenon) examples
and a build file to compile and run them.

Requirements
------------

* Copy of this repository
* Java JDK version 7 or greater.
* An internet connection to download dependencies



Running the examples from the Linux command line
------------------------------------------------

```
# install version management software git
sudo apt-get install git

# get a copy of this repository
git clone https://github.com/NLeSC/Xenon-examples.git

# change into the new directory:
cd Xenon-examples
```

When running from the command line, the examples need to be compiled first. We have provided an easy way to do so through:
```
# (in Xenon-examples/)
./gradlew
```

Which will generate a new file 'build/libs/Xenon-examples-all.jar' containing the compiled examples and their dependencies.

Whenever you make changes to any of the examples, re-run `./gradlew` to update the jar file.

After the jar has been generated, examples can be executed using the following format:
```
# (in Xenon-examples/)
java -cp <jar file> <fully qualified example main class> <arguments required by example>
```

For example the `DirectoryListing` example from the `nl.esciencecenter.xenon.examples.files` package can be run with (Linux):
```
# (in Xenon-examples/)
java -cp build/libs/Xenon-examples-all.jar nl.esciencecenter.xenon.examples.files.DirectoryListing file:///tmp
```

'[run-examples.sh](https://github.com/NLeSC/Xenon-examples/blob/master/run-examples.sh)' is a Bash script that contains a number of example calls; execute `./run-examples.sh` at the command line to run them all. Note that some of the examples require passwordless ssh login to localhost (read [this](doc/passwordless-ssh-to-localhost.md) if you don't know how to set that up).

Running examples from the IDE
-----------------------------

Generate IDE-specific project files with `./gradlew eclipse` or `./gradlew idea` and subsequently import the project into Eclipse or IntelliJ IDEA using their respective import functionality.

Example files can be opened and run from inside the IDE, without the need to re-compile using `./gradlew`. You do need to have run ``./gradlew`` at least once though before you can run any of the examples from within the IDE, just to make sure that all the dependencies have been downloaded from the internet.

Run examples against local version of Xenon library
---------------------------------------------------

You made changes to a local version of the Xenon library and want to make sure the examples work use the following steps:

1. Goto the repository containing local Xenon library
2. Make sure the version of the Xenon library defined in `Xenon/gradle/common.gradle` and `Xenon-examples/build.gradle` are the same.
3. Run `./gradlew publishToMavenLocal`, this will install the Xenon library in the local Maven repository
4. Go back to this (Xenon-examples) repository
5. The gradlew commands will use the version of the Xenon library installed in the local Maven repository

Tutorial
--------

A tutorial pdf targeting inexperienced users is available [here](https://github.com/NLeSC/Xenon-examples/raw/master/doc/tutorial/xenon-tutorial.pdf).
