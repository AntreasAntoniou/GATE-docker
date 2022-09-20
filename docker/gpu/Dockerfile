FROM gcr.io/deeplearning-platform-release/pytorch-gpu:latest

SHELL ["/bin/bash", "-c"]

RUN apt-get update  \
    && apt-get install -y --no-install-recommends \
        libgl1 \
        libglib2.0-0
RUN conda init bash
RUN conda create -n capit python=3.8 -y
RUN echo "conda activate capit" >> ~/.bashrc

RUN git clone https://github.com/AntreasAntoniou/CAPMultiModal.git

SHELL ["conda", "run", "-n", "capit", "/bin/bash", "-c"]

RUN cd CAPMultiModal \
    && conda install -c conda-forge mamba -y \
    && bash install_dependencies.sh

CMD ["bin/bash"]