FROM gcr.io/tpu-pytorch/xla:nightly_3.8_tpuvm

SHELL ["/bin/bash", "-c", "source ~/.bashrc"]

RUN conda install python=3.8 -y
RUN conda install -c conda-forge mamba -y
RUN echo "conda activate" >> ~/.bashrc

RUN git clone https://github.com/AntreasAntoniou/CAPMultiModal.git


SHELL ["/bin/bash", "-c", "source ~/.bashrc", "conda", "run", "-n", "base", "/bin/bash", "-c"]

RUN cd CAPMultiModal  \
    && bash install_dependencies.sh

CMD ["bin/bash"]