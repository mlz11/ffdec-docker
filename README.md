# ffdec-docker

Headless [FFDec (JPEXS Free Flash Decompiler)](https://github.com/jindrapetrik/jpexs-decompiler) in Docker. No need to install Java or FFDec locally.

## Build

```bash
docker build -t ffdec .
```

## Usage

FFDec CLI is the entrypoint, so you can pass arguments directly:

```bash
docker run --rm -v ./input:/work/input -v ./output:/work/output ffdec [args]
```

See the [FFDec CLI reference](https://github.com/jindrapetrik/jpexs-decompiler/wiki/Commandline-arguments) for all available arguments.

## FFDec version

This image uses FFDec 21.0.1.
