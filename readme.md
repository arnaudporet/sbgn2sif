# Converting SBGN encoded pathways to the SIF file format

Copyright 2019-2020 [Arnaud Poret](https://github.com/arnaudporet)

Licensed under the [Apache License Version 2.0](https://www.apache.org/licenses/LICENSE-2.0) (the "License").

You may not use this file except in compliance with the License.

You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0.

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.

See the License for the specific language governing permissions and limitations under the License.

## sbgn2sif

Convert SBGN encoded pathways to the SIF file format.

sbgn2sif is currently quite lazy. It only requires:

* glyphs with IDs (in SBGN, glyphs are nodes)
* glyphs with labels (i.e. node names)
* arcs with IDs (in SBGN, arcs are edges)
* arcs with classes (i.e. edge types)
* arcs with valid source glyphs (cf. above)
* arcs with valid target glyphs (cf. above)

If a glyph has more than one label then its name is the list of its labels separated with "||".

If a SBGN file contains more than one map then they are processed independently.

XML namespace is ignored, if any.

For explanations about the SBGN file format see https://sbgn.github.io.

For explanations about the SIF file format see at the and of this readme file.

### Requirements

* [Python 3](https://www.python.org)
* a unix based operating system

### Usage

Ensure that sbgn2sif is executable:

```sh
chmod ugo+rx sbgn2sif
```

Usage: `sbgn2sif [-h] <sbgnfile> [<sbgnfile> ...]`

Positional arguments:

* `<sbgnfile>`: a SBGN encoded pathway

Optional arguments:

* `-h/--help`: print help

## Examples

These examples come from downloaded [Reactome pathways](https://reactome.org/PathwayBrowser/).

### Signaling by EGFR:

```sh
./sbgn2sif examples/Signaling_by_EGFR/Signaling_by_EGFR.sbgn
```

### Signaling by Insulin receptor:

```sh
./sbgn2sif examples/Signaling_by_Insulin_receptor/Signaling_by_Insulin_receptor.sbgn
```

### Intrinsic Pathway for Apoptosis:

```sh
./sbgn2sif examples/Intrinsic_Pathway_for_Apoptosis/Intrinsic_Pathway_for_Apoptosis.sbgn
```

### RAF/MAP kinase cascade:

```sh
./sbgn2sif examples/RAF_MAP_kinase_cascade/RAF_MAP_kinase_cascade.sbgn
```

### PIP3 activates AKT signaling:

```sh
./sbgn2sif examples/PIP3_activates_AKT_signaling/PIP3_activates_AKT_signaling.sbgn
```

## The SIF file format

In a SIF file encoding a network, each line encodes an edge as follows:

```
source \t interaction \t target
```

Note that the field separator is the tabulation: the SIF file format is the tab separated values format (TSV) with exactly 3 columns.

For example, the edge representing the activation of RAF1 by HRAS is a line of a SIF file encoded as follows:

```
HRAS \t activation \t RAF1
```
