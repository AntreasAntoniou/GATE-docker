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
    && bash install_dependencies.sh

RUN apt install fish -y \
    && curl -sS https://starship.rs/install.sh | sh -y \
    && starship init fish | source

RUN apt install libgl1-mesa-glx -y
RUN apt-get install 'ffmpeg'\
    'libsm6'\
    'libxext6'  -y

CMD ["bin/bash"]