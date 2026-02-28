# ffdec-docker

Headless [FFDec (JPEXS Free Flash Decompiler)](https://github.com/jindrapetrik/jpexs-decompiler) in Docker. Useful for batch-processing SWF files without installing Java or FFDec locally.

## Build

```bash
docker build -t ffdec .
```

## Usage

FFDec CLI is the entrypoint, so you can pass arguments directly.

### Export SWF frames to PNG

```bash
docker run --rm -v ./input:/work/input -v ./output:/work/output ffdec \
  -export frame /work/output /work/input/file.swf
```

### Export with zoom (1000%)

```bash
docker run --rm -v ./input:/work/input -v ./output:/work/output ffdec \
  -zoom 10 -export frame /work/output /work/input/file.swf
```

### Export as SVG

```bash
docker run --rm -v ./input:/work/input -v ./output:/work/output ffdec \
  -format frame:svg -export frame /work/output /work/input/file.swf
```

### Export all SWFs in a directory

```bash
for f in ./input/*.swf; do
  name=$(basename "$f" .swf)
  docker run --rm -v ./input:/work/input -v ./output:/work/output ffdec \
    -zoom 10 -export frame "/work/output/$name" "/work/input/$(basename "$f")"
done
```

### Long-running container

If you're processing many files, avoid container startup overhead by keeping one alive:

```bash
docker run -d --name ffdec-worker ffdec -help  # start and keep alive
# Then exec into it:
docker exec ffdec-worker java -jar /opt/ffdec/ffdec.jar \
  -export frame /work/output /work/input/file.swf
```

## FFDec CLI reference

See the [FFDec wiki](https://github.com/jindrapetrik/jpexs-decompiler/wiki/Commandline-arguments) for all available CLI arguments.

## FFDec version

This image uses FFDec 21.0.1.
