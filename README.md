# @hishprorg/vero-optio
[![NPM version](https://img.shields.io/npm/v/@hishprorg/vero-optio.svg)](http://npmjs.com/package/@hishprorg/vero-optio)
[![Build Status](https://github.com/hishprorg/vero-optio/actions/workflows/ci.yml/badge.svg)](https://github.com/hishprorg/vero-optio/actions/workflows/)
[![Gitpod ready-to-code](https://img.shields.io/badge/Gitpod-ready--to--code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/hishprorg/vero-optio)

A simple command line Node.js tool to read and write NBT files to JSON and back. Supports big, little and little-varint encoding.

Uses `prismarine-nbt` for serialization and deserialization, see https://github.com/PrismarineJS/prismarine-nbt for more info on schema.

### Usage 

via npx:
```sh
npx @hishprorg/vero-optio --help
```

via npm:
```
npm install -g @hishprorg/vero-optio
@hishprorg/vero-optio --help
```

```
usage, feel free to use natural language:
Parse an NBT file to JSON: 
    @hishprorg/vero-optio <path-to-nbt-file> [out-json-file] [little|big|varint]

    @hishprorg/vero-optio level.dat
        (Dump the contents of level.dat to terminal)
    @hishprorg/vero-optio level.dat to level.json
        (Dump the contents of level.dat to JSON)
    @hishprorg/vero-optio level.dat as little to level.json
        (Dump the contents of little endian encoded level.dat to JSON)

Write an JSON file to uncompressed NBT (defaults to big endian):
    @hishprorg/vero-optio write <path-to-json> [out-nbt-file] [little|big|varint]

    @hishprorg/vero-optio write level.json to level.dat
    @hishprorg/vero-optio write level.json to level.dat as little

You can also pipe the input to @hishprorg/vero-optio:
    cat level.dat | @hishprorg/vero-optio
    cat level.dat | @hishprorg/vero-optio to level.json
    cat level.json | @hishprorg/vero-optio write
    cat level.json | @hishprorg/vero-optio write to level.dat
```

### Example

If you do not specify endianness, it will automatically be inferred.

Parse to json, and back to nbt as big endian
```sh
$ @hishprorg/vero-optio level.dat level.json
* Dumping NBT file "file.nbt" to "file.json" as JSON
(as big endian)
$ @hishprorg/vero-optio write level.json level.dat
* Writing JSON from "file.json" to "file.nbt" as big endian
written!
```

Write as little endian
```sh
$ @hishprorg/vero-optio level.dat level.json
* Dumping NBT file "file.nbt" to "file.json" as JSON
(as big endian)
$ @hishprorg/vero-optio write level.json level.dat little
* Writing JSON from "file.json" to "file.nbt" as little endian
```
