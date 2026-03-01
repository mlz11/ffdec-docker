# ffdec-docker

Headless [FFDec (JPEXS Free Flash Decompiler)](https://github.com/jindrapetrik/jpexs-decompiler) in Docker. No need to install Java or FFDec locally.

## Quick start

```bash
docker pull mlz11/ffdec
docker run --rm -v ./input:/work/input -v ./output:/work/output mlz11/ffdec [args]
```

## Build locally

```bash
docker build -t ffdec .
```

## Usage

FFDec CLI is the entrypoint, so you can pass arguments directly:

```bash
docker run --rm -v ./input:/work/input -v ./output:/work/output mlz11/ffdec [args]
```

See the [FFDec CLI reference](https://github.com/jindrapetrik/jpexs-decompiler/wiki/Commandline-arguments) for all available arguments.

## FFDec version

This image uses FFDec 25.1.2.

This Dockerfile was [adopted upstream](https://github.com/jindrapetrik/jpexs-decompiler/releases/tag/nightly3440) starting with nightly build 3440.
