FROM gcr.io/deeplearning-platform-release/pytorch-gpu:latest

SHELL ["/bin/bash", "-c"]

RUN apt-get update  \
    && apt-get install -y --no-install-recommends \
        libgl1 \
        libglib2.0-0
RUN conda init bash
RUN conda create -n gate python=3.8 -y
RUN echo "conda activate gate" >> ~/.bashrc

RUN git clone https://github.com/AntreasAntoniou/GATE.git

SHELL ["conda", "run", "-n", "gate", "/bin/bash", "-c"]

RUN cd GATE \
    && conda install -c conda-forge mamba -y \
    && mamba install pytorch torchvision torchaudio cudatoolkit=11.6 -c pytorch -c conda-forge
    && bash install_dependencies.sh

CMD ["bin/bash"]