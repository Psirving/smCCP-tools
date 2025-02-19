Modernize smCCP tool installation
=================================

This folder contains a devcontainer which installs Python3 compatible versions of:

- StructureAnalysisTools: Psirving/StructureAnalysisTools:python3
- RingMapper: Weeks-UNC/RingMapper:python3
- DanceMapper: MustoeLab/DanceMapper:python3

With all dependencies:

- RNAstructure: Fold, partition, ProbabilityPlot, ShapeKnots
- Python 3.8: cython, pandas, scipy, pybedtools, matplotlib, requests

Because these now live on the path, all modules are packaged in a parent module to not clutter the namespace. Python parent module names:

- StructureAnalysisTools: `rnastruct`
    - e.g. `import rnastruct.ArcPlot as ArcPlot` replaces `import ArcPlot`
    - note: parent module is empty, i.e. `import rnastruct` is not useful.
- RingMapper: `smccp`
- DanceMapper: `dance`

All command line scripts now live on the path, e.g.:

- `ArcPlot.py -h` replaces `python /path/to/ArcPlot.py -h`
