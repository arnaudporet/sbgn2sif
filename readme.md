# Converting SBGN-encoded pathways to the SIF file format

Copyright 2019 [Arnaud Poret](https://github.com/arnaudporet)

This work is licensed under the [Apache License Version 2.0](https://www.apache.org/licenses/LICENSE-2.0) (the "License"). You may not use this work except in compliance with the License. You may obtain a copy of the License at https://www.apache.org/licenses/LICENSE-2.0.

## sbgn2sif

Converts SBGN-encoded pathways to the SIF file format.

For information about the SBGN file format, please see https://sbgn.github.io.

For information about the SIF file format, please see at the end of this readme file.

### Requirements

* [Python 3](https://www.python.org)
* a unix-based operating system

### Usage

`sbgn2sif [-h] [-l] sbgnfile [sbgnfile ...]`

Ensure that `sbgn2sif` is executable: `chmod ugo+x sbgn2sif`.

Positional arguments:

* `sbgnfile`: a SBGN file

Optional arguments:

* `-l/--license`: print the [Apache License Version 2.0](https://www.apache.org/licenses/LICENSE-2.0) under which sbgn2sif is
* `-h/--help`: print help

sbgn2sif is currently quite lazy. It only requires:

* glyphs with IDs (in SBGN, glyphs are nodes)
* glyphs with labels (i.e. node names)
* arcs with IDs (in SBGN, arcs are edges)
* arcs with classes (i.e. edge types)
* arcs with valid source glyphs (cf. above)
* arcs with valid target glyphs (cf. above)

If a glyph has more than one label, then its name is the list of its labels separated with "||".

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

Note that the field separator is the tabulation `\t`: the SIF file format is the tab-separated values format (TSV) with exactly 3 columns.

For example, the edge representing the _activation_ of _RAF1_ by _HRAS_ is a line of a SIF file encoded as follows:

```
HRAS \t activation \t RAF1
```
