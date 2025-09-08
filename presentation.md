---
theme: default
---
<style>
table {
  font-size: 20px;
}
td {
    white-space: nowrap;
}
ul {
  font-size: 30px;
}
</style>
## JBang! 
### Java Scripting the Way It Was Meant to Be

![](deck-assets/jbang.png)<!-- .element height="250px"  -->

Jason Lee - Principal Software Engineer, IBM

https://jasondl.ee - jason@steeplesoft.com

---
## About Me

- [~]Software developer since 1997
- [~]Principal Software Engineer at IBM
- [~]President of the [Oklahoma City Java Users Group](https://okcjug.org)
- [~]Java Champion
- [~]Author - [Java 9 Programming Blueprints](https://www.packtpub.com/application-development/java-9-programming-blueprints)
- [~]Blogger - [https://jasondl.ee](https://jasondl.ee)
- [~]Misc: Martial Arts (BJJ and Karate), Bass Guitar, Smoking Meats

---
<!-- .element data-background="deck-assets/seine.jpg" -->

---
<!-- .element data-background="deck-assets/sophie.jpg" -->

---
## What we'll cover
- What is JBang?
- Getting Started
- Writing Scripts
- Quasi-advanced Topics

---
## What is JBang?

- [~]JBang is a tool that makes it easy to write and run Java scripts without the traditional setup overhead
- [~]Inspired by the new shebang (#!) feature support in Java 10<br>`#!/usr/bin/java --source 21`
- [~]'From there came j’bang which is a "bad" spelling of how shebang is pronounced in French.'

---
## Installation

###  Manual Install
- [~] Unzip the [latest binary release](https://github.com/jbangdev/jbang/releases/latest)
- [~] Add `jbang-<version>/bin` to your $PATH 

---
## Installation (cont)

###  Using Package Managers
- JBang: <br>`curl -Ls https://sh.jbang.dev | bash -s - app setup`
- JBang (Windows): <br>`iex "& { $(iwr -useb https://ps.jbang.dev) } app setup"`
- SDKMAN!: `sdk install jbang`
- Homebrew: `brew install jbang`
- Others: RPM, Docker, Chocolatey, Scoop, NPM, PIP

---
## Your First Script

```shell
$ jbang init demo.java
$ jbang demo.java
Hello World!
```
[~]✌️ Easy Peasy 

---
### Generated Code

```java[1|3|5|6-8]
///usr/bin/env jbang "$0" "$@" ; exit $?

import static java.lang.System.*;

public class demo {
    public static void main(String... args) {
        out.println("Hello World");
    }
}
```

---
## A "Real" Script

- [~] Maven Central search
- [~] Search for a variety of parameters
  - [~] Class name
  - [~] Fully-qualified class name
  - [~] Group ID
  - [~] Artifact ID
- [~] Specify number of rows to display

---
## JBang Templates

JBang comes with a number of templates that you can use to get started quickly.
|Template|Description|
|--------|-----------|
|agent|Agent template|
|cli|CLI template|
|gpt|Template using ChatGPT (requires --preview and OPENAI_API_KEY)|
|hello|Basic Hello World template|
|jbang-catalog|Template for creating a new JBang catalog hosted on github with automatic renovate updates|
|qcli|Quarkus CLI template|
|qrest|Quarkus REST template|

---
## Introducing mvnsrch

```shell
$ jbang -t cli mvnsrch.java
$ jbang mvnsrch.java --help
Usage: mvnsrch [-hV] <greeting>
mvnsrch made with jbang
      <greeting>   The greeting to print
  -h, --help       Show this help message and exit.
  -V, --version    Print version information and exit.
$ jbang edit -b mvnsrch.java
```

---
## JBang Directives

- [~] Dependencies and Repositories 
  - [~] `//DEPS` - Declares Maven dependencies for your script
  - [~] `//REPOS` - Specifies additional Maven repositories
- [~] Language Version and Features
  - [~] `//JAVA` - Specifies the Java version requirement
  - [~] `//PREVIEW` - Enable preview JDK features
  - [~] `//KOTLIN` - Specifies Kotlin compiler version
  - [~] `//GROOVY` - Specifies Groovy compiler version

---
## JBang Directives (cont)
- [~] Misc
  - [~] `//MAIN` - Override the default entry point
  - [~] `//DESCRIPTION` - Provide default description for script
  - [~] `//SOURCES` - Includes additional source files in compilation
  - [~] `//FILES` - Includes additional files in the script execution environment
  - [~] `//DOCS` - Links to additional documentation resources for the script.

---
## Quasi-Advanced Topics

### Aliases
- [~]Aliases enable easy launch of jbang scripts
- [~]Provides a shorthand to avoid remembering the full path to the script
- [~]Ex: `jbang alias add --name hello https://github.com/jbangdev/jbang-examples/blob/HEAD/examples/helloworld.java`
- [~]Run with `jbang hello`

---
### JBang Apps

- [~] JBang Apps allow you to install scripts as a system command, allowing you to run them from anywhere
- [~] First step: `jbang app setup`
- [~] Next: `jbang app install --name hello https://github.com/jbangdev/jbang-examples/blob/HEAD/examples/helloworld.java`
- [~] Run with `hello`

---
### JBang Catalogs

- [~]Catalogs are lists of Aliases
- [~]_Can_ be remote, but make sure you trust the source!
- [~]`jbang catalog list`
- [~]`jbang catalog add [--name <name>] <url>`
- [~]`jbang alias list <catalog>`

---
### JBang Summary

- Tool for writing easy-to-run command line scripts in Java
- Leverages existing Java tooling and ecosystem
- Supports external dependencies and resources
- Easily shareable through remote catalogs
