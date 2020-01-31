# Arguments to select python version, cuda version etc.
# These were added here using a shell script that generated this file. Changing this file is not recommended.
ARG base_image=ubuntu:16.04

FROM ${base_image}

ARG python_version=3.7.2
# DON'T CHANGE THIS ARG
ARG username=python_user

# Add this to prevent prompts during build
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update

# install pyenv pre-requisites
RUN apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python-openssl git

# Switch user from root
RUN useradd -m ${username}
USER ${username}

# get pyenv
RUN git clone https://github.com/pyenv/pyenv.git /home/${username}/.pyenv

# Set up environment variables for pyenv
ENV HOME /home/${username}
ENV PYENV_ROOT $HOME/.pyenv
ENV PATH $PYENV_ROOT/shims:$PYENV_ROOT/bin:$PATH

# Install specific python version
RUN pyenv install ${python_version}
RUN pyenv global ${python_version}
RUN pyenv rehash

# Upgrade pip
RUN pip install -U pip

# Check if system python was updated properly
# ADD ./src/info.py .
# RUN python info.py
# CMD ["python", "src/info.py"]

# Install jupyter and jupyter notebook
RUN pip install jupyter
RUN pip install jupyter notebook

# Set up port for jupyter
EXPOSE 8888

# change working directory inside container
WORKDIR /home/${username}/app/

# Project specific stuff
COPY requirements.txt .
RUN pip install -r requirements.txt

# Please add any custom linux packages installed or any other custom environment setup steps here
# Switch user to root if need root privilege and switch it back
# USER root
# Example: 
# USER root
# RUN apt-get install build-essential
# USER ${username}
# END of environment setup

# Run jupyter lab
CMD [ "jupyter", "notebook", "--ip", "0.0.0.0", "--port", "8888", "--NotebookApp.custom_display_url=http://127.0.0.1:8888", "--no-browser"]
# CMD [ "jupyter", "lab", "--no-browser"]
