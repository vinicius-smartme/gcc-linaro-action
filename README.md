![GitHub Release](https://img.shields.io/github/v/release/vinicius-smartme/gcc-linaro-action) ![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/vinicius-smartme/gcc-linaro-action/.github%2Fworkflows%2Ftest.yml)


## What is gcc-linaro?

The [GCC-linaro](https://releases.linaro.org/components/toolchain/gcc-linaro/) is a [GCC](https://gcc.gnu.org/) based toolchain for 
ARM devices developed by the [Linaro](https://www.linaro.org/).

## What is this action for?

The `gcc-linaro action` goal is to install a GCC-Linaro based toolchain (which includes the cross compiler) on a github 
workflow. As the installation of cross compilers and toolchains on [GNU/Linux](https://www.gnu.org/gnu/linux-and-gnu.html) OSs is quite easy and strait forward, this 
action is focused on Windows OS only, which requires more steps for download and installation.

## How to use it?

Add the `gcc-linaro-action` on your github workflow with the desired toolchain.

### Usage example

```yml
name: Test GCC-Linaro Action

on:
  push:
    branches:
      - '**'
  pull_request:
    branches:
      - '**'

jobs:
  test:
    runs-on: windows-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Install the GCC Linaro toolchain
        uses: vinicius-smartme/gcc-linaro-action@v1
        with:
          version: '5'
          toolchain: 'arm-linux-gnueabihf'
      
      - name: Verify the GCC cross compiler
        run: |
          arm-linux-gnueabihf-gcc --version

      - name: Run a sample build command
        run: |
          # Creates a hello.c file
          echo '#include <stdio.h>' > hello.c
          echo 'int main() {' >> hello.c
          echo '    printf("Hello, ARM world!\\n");' >> hello.c
          echo '    return 0;' >> hello.c
          echo '}' >> hello.c
          arm-linux-gnueabihf-gcc -o hello hello.c
```

### Input options (required)

| Option | Value | Description | Default |
| :--- | :--- | :--- | :--- |
| **version**  | 4, 5, 6 or 7 | The selected latest release toolchain version | `7` |
| **toolchain** | `aarch64-elf`, `aarch64-linux-gnu`, `aarch64_be-elf`, `aarch64_be-linux-gnu`, `arm-eabi`, `arm-linux-gnueabi`, `arm-linux-gnueabihf`, `armeb-eabi`, `armeb-linux-gnueabi`, `armeb-linux-gnueabihf` or `armv8l-linux-gnueabihf`| The ARM toolchain | - |

## License

> GLP-3.0 License

THERE IS NO WARRANTY FOR THE PROGRAM, TO THE EXTENT PERMITTED BY
APPLICABLE LAW.  EXCEPT WHEN OTHERWISE STATED IN WRITING THE COPYRIGHT
HOLDERS AND/OR OTHER PARTIES PROVIDE THE PROGRAM "AS IS" WITHOUT WARRANTY
OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO,
THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
PURPOSE.  THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE PROGRAM
IS WITH YOU.  SHOULD THE PROGRAM PROVE DEFECTIVE, YOU ASSUME THE COST OF
ALL NECESSARY SERVICING, REPAIR OR CORRECTION.

> Copyright (C) 2007 Free Software Foundation, Inc. <https://fsf.org/>

## Thanks

None of this would be possible without the [GCC](https://gcc.gnu.org/), [GNU](https://www.gnu.org/home.en.html), 
[Free Software Foundation](https://www.fsf.org/), the [Linux Foundation](https://www.linuxfoundation.org/), the [Linaro](https://www.linaro.org/) and the innumerable __Unknown Open Source contributors__. 
Many thanks for the strong open source contribution.

## Contributions

Any contribution is welcome.

