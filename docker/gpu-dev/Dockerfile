FROM gcr.io/deeplearning-platform-release/pytorch-gpu:latest

SHELL ["/bin/bash", "-c"]

RUN apt-get update
RUN conda init bash
RUN conda create -n gate python=3.10 -y
RUN echo "conda activate gate" >> ~/.bashrc

RUN git clone https://github.com/AntreasAntoniou/GATE.git

SHELL ["conda", "run", "-n", "gate", "/bin/bash", "-c"]

RUN cd GATE \
    && conda install -c conda-forge mamba -y \
    && mamba install pytorch torchvision torchaudio cudatoolkit=11.6 -c pytorch -c conda-forge \
    && bash install_dependencies.sh \
    && apt install fish -y \
    && curl -sS https://starship.rs/install.sh | sh \
    && starship init fish | source \

CMD ["bin/bash"]