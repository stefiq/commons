# `commons` 📦

## Description

`commons` is a Python 3 library containing useful implementations for all CRS modules:

- utility functions and classes
- interfaces
- enumerations

The enumerations are not exhaustive.
They define the minimal set of members that are used in OpenCRS.
For example, `InputStreams` doesn't define an `ENVIRONMENT_VARIABLE` (a valid input stream for an executable) as this case is not tacked yet by the project.

## Setup

1. Make sure you have set up the repositories and Python environment according to the [top-level instructions](https://github.com/open-crs#requirements). That is:

   * Docker is installed and is properly running. Check using:

     ```console
     docker version
     docker ps -a
     docker run --rm hello-world
     ```

     These commands should run without errors.

   * The current repository and the [`commons` repository](https://github.com/open-crs/commons) are cloned (with submodules) in the same directory.

   * uv is installed. Check using:

     ```console
     uv --version
     ```

2. Create the virtual environment:

   ```console
   uv venv
   ```

3. Install the required packages based on `pyproject.toml`:

   ```console
   uv sync
   ```

4. Build the [Ghidra](https://ghidra-sre.org/) and [QBDI](https://github.com/QBDI/QBDI) Docker images used by other modules:

   ```console
   docker build --tag ghidra -f commons/ghidra/docker/Dockerfile commons/ghidra/docker
   docker build --platform linux/386 --tag qbdi_args_fuzzing -f commons/qbdi/docker/Dockerfile commons/qbdi/docker
   ```
