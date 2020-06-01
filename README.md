![Build](https://github.com/d-asnaghi/bazel-arm-none-eabi/workflows/Build/badge.svg)

# Bazel arm-none-eabi-gcc toolchain 

The goal of the project is to illustrate how to use a custom ARM embedded toolchain with Bazel. 

If this project was useful to you, give it a ⭐️ and I'll keep improving it!

You can follow the post [Bazel for ARM embedded toolchains](https://d-asnaghi.github.io/blog/post/embedded-bazel/) to get more details about this code.

## Instructions

### Bazel

[Install Bazel](https://docs.bazel.build/versions/master/install.html) for your platform. Installing with a package manager is recommended, especially on windows where additional runtime components are needed.

- [Ubuntu Linux](https://docs.bazel.build/versions/master/install-ubuntu.html): `sudo apt install bazel`
- [macOS](https://docs.bazel.build/versions/master/install-os-x.html): `brew install bazel`
- [Windows](https://docs.bazel.build/versions/master/install-windows.html): `choco install bazel`
  
### Bazelisk

`bazelisk` is a user-friendly launcher for `bazel`. Follow the install instructions in the [Bazelisk repo](https://github.com/bazelbuild/bazelisk)

Use `bazelisk` as you would use `bazel`, this takes care of using the correct Bazel version for each project by using the [.bazelversion](./.bazelversion) file contained in each project.

  
### Build

Use this command to build the `project` target.

```bash
# build the project
bazelisk build project
```

This will take care of downloading the appropriate toolchain for your OS and compile all the source files specified by the target.

## Folder structure

```bash
├── WORKSPACE
│
├── project
│   ├── BUILD.bazel
│   └── /* SOURCE CODE */
│
└── toolchains
    ├── BUILD.bazel
    └── arm-none-eabi
        ├── darwin
        │   └── /* DARWIN TOOLCHAIN */
        ├── linux
        │   └── /* LINUX TOOLCHAIN  */
        └── ...
            └── /* OTHER TOOLCHAIN  */

```