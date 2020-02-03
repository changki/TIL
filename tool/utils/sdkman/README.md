# SDKMAN

reference
- https://sdkman.io/
- https://github.com/sdkman/sdkman-cli
- [SDK! 으로 Java 버전 관리하기](https://phoby.github.io/sdkman/)

## Infomation

```
Unix 기반 시스템에서 여러 소프트웨어 개발 키트의 병렬 버전을 관리하기 위한 도구.
설치, 전환, 제거 및 나열하기 위한 편리한 CLI 및 API를 제공.
```

## Installation

1. Dependence Package

    `unzip, zip, curl, sed, which`

2. install sdkman

    Open your favourite terminal and enter the following:
    ```
    $ curl -s https://get.sdkman.io | bash
    ```

3. install check

    ```
    $ sdk v

    SDKMAN 5.7.4+362
    ```

## SDKMAN options

```
Usage: sdk <command> [candidate] [version]
       sdk offline <enable|disable>

   commands:
       install   or i    <candidate> [version] [local-path]
       uninstall or rm   <candidate> <version>
       list      or ls   [candidate]
       use       or u    <candidate> <version>
       default   or d    <candidate> [version]
       current   or c    [candidate]
       upgrade   or ug   [candidate]
       version   or v
       broadcast or b
       help      or h
       offline           [enable|disable]
       selfupdate        [force]
       update
       flush             <broadcast|archives|temp>

   candidate  :  the SDK to install: groovy, scala, grails, gradle, kotlin, etc.
                 use list command for comprehensive list of candidates
                 eg: $ sdk list
   version    :  where optional, defaults to latest stable if not provided
                 eg: $ sdk install groovy
   local-path :  optional path to an existing local installation
                 eg: $ sdk install groovy 2.4.13-local /opt/groovy-2.4.13
```

## Uninstallation

```
$ rm -rf ~/.sdkman
```

`.bashrc`, `.zshrc` delete sdk options


