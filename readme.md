# Converting SBGN-encoded pathways to the SIF file format

Copyright 2019 [Arnaud Poret](https://github.com/arnaudporet)

This work is licensed under the [Apache License Version 2.0](https://www.apache.org/licenses/LICENSE-2.0) (the "License"). You may not use this work except in compliance with the License. You may obtain a copy of the License at https://www.apache.org/licenses/LICENSE-2.0.

## sbgn2sif

Convert SBGN-encoded pathways to the SIF file format.

For information about the SBGN file format see https://sbgn.github.io.

For information about the SIF file format see at the end of this readme file.

### Requirements

* [Python 3](https://www.python.org)
* a unix-based operating system

### Usage

Ensure that `sbgn2sif` is executable:

```sh
chmod ugo+x sbgn2sif
```

Usage: `sbgn2sif [-h] <sbgnfile> [<sbgnfile> ...]`

Positional arguments:

* `<sbgnfile>`: a SBGN-encoded pathway

Optional arguments:

* `-h/--help`: show help and exit

sbgn2sif is currently quite lazy. It only requires:

* glyphs with IDs (in SBGN, glyphs are nodes)
* glyphs with labels (i.e. node names)
* arcs with IDs (in SBGN, arcs are edges)
* arcs with classes (i.e. edge types)
* arcs with valid source glyphs (cf. above)
* arcs with valid target glyphs (cf. above)

If a glyph has more than one label then its name is the list of its labels separated with "||".

## Examples

These examples come from downloaded [Reactome](https://reactome.org/PathwayBrowser/) pathways.

### Signaling by EGFR:

```sh
./sbgn2sif examples/Signaling_by_EGFR/Signaling_by_EGFR.sbgn
```

### Signaling by Insulin receptor:

```sh
./sbgn2sif examples/Signaling_by_Insulin_receptor/Signaling_by_Insulin_receptor.sbgn
```

## The SIF file format

In a SIF file encoding a network, each line encodes an edge as follows:

```
source \t interaction \t target
```

Note that the field separator is the tabulation: the SIF file format is the tab-separated values format (TSV) with exactly 3 columns.

For example, the edge representing the activation of RAF1 by HRAS is a line of a SIF file encoded as follows:

```
HRAS \t activation \t RAF1
```
