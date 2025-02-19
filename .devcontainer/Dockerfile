# from official python3 image
FROM python:3.8

# update pip
# pip install cython, pandas, matplotlib, scipy, requests
# pip install python3 branches of StructureAnalysisTools (psirving fork), RingMapper, and DanceMapper
RUN pip install --upgrade pip \
    && pip install --no-cache-dir cython pandas matplotlib scipy requests pybedtools \
    && pip install --no-cache-dir git+https://github.com/Psirving/StructureAnalysisTools.git@python3 \
    && pip install --no-cache-dir git+https://github.com/Weeks-UNC/RingMapper.git@python3 \
    && pip install --no-cache-dir git+https://github.com/MustoeLab/DanceMapper.git@python3

# install build essentials
# TODO: it is not recommended to install build essentials in production container
# correct pattern is FROM ubuntu:20.04 AS builder, build, copy what is needed to runtime container
RUN apt-get update \
    && apt-get install -y build-essential \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# # Install RNAstructure
# # TODO: This layer is kind of big
RUN wget https://rna.urmc.rochester.edu/Releases/current/RNAstructureLinuxTextInterfaces64bit.tgz -O /tmp/RNAstructureLinuxTextInterfaces64bit.tgz \
    && tar -C /usr/local -xvf /tmp/RNAstructureLinuxTextInterfaces64bit.tgz \
    && rm /tmp/RNAstructureLinuxTextInterfaces64bit.tgz
WORKDIR /usr/local/RNAstructure
RUN make ProbabilityPlot partition Fold ShapeKnots
ENV PATH=$PATH:/usr/local/shapemapper2-2.3:/usr/local/RNAstructure/exe
