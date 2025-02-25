# How to utilize the QoL tools in the repository

## Markdown lint tool

### Command usage: markdownlint [options] <file|directory|glob>

Use this command to check any markdown files in the repository for errors and poor usage of markdown. By default, it ignores lines that may be "too long" in length before
a new line is started. Ignores the styles folder (based on current configuration) that the Vale tool creates during the markdownlint execution, in case of doing full-repo
markdown linting

For options, the main relevant ones include:
- -d: includes files that start with a . in the program's execution
- -f: automatically fixes basic errors
- -i <file|directory|glob>: ignores the file(s) in the given path during the current execution
- -j: writes the output of the program in JSON format
- -o <outputFile>: write sthe output of the program into a separate file (no results in terminal)
- -r <file|directory|glob|package>: include custom rule files (default: [])
- -h: outputs help with the program onto console (includes full list of options among other descriptors of the program)

The program also includes 5 exit codes to mark the results of the program's execution:

- 0: succesful run of the program
- 1: linting errors
- 2 (requires -o): unable to write to specified output file
- 3 (requires -r): unable to load the provided custom rule(s)
- 4: unexpected error, such as malformed config)

## Grammar and spelling checker

### Command usage: vale [options] <file|directory|glob>

Use this command to check the syntax (grammar, spelling, etc.) of the specified files based on some set of styles given to the program (listed below). The output (warnings
and suggestions) is printed onto the console. Current configuration ignores the styles folder that the program creates during execution, in case of doing full-repo grammar
checking.

#### Main style used: Google Developer Documentation Style Guide
#### Supplementary style used: write-good
#### Config options: MDX

For options, the main relevant ones include:

- sync: download and install pacakges to stay up to date with current versions
- ls-config: print in JSON format the current config of the program
- ls-dirs: print the location of default configuration directories
- --config='path to file': override the default config search process, specifying a certain config file to be used instead
- --filet='filter type': add an expression to filter runs by
- --ignore-syntax: treat the inputted text/files as plain text
- --version: check the Vale version currently installed

The program also includes 3 exit codes to mark the results of the program's execution:

- 0: no error(s) were found
- 1: linting error(s) occured, can be disabled with --no-exit
- 2: runtime error(s)
