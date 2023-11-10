# - Author: Giorgio Simonini, Simone Tolomei - #

FROM ubuntu:22.04

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \ 
    && apt-get install -y \
    git \
    nano \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Create a new user
ARG USERNAME=pydev
ARG USER_UID=1000
ARG USER_GID=${USER_UID}
RUN groupadd --gid ${USER_GID} ${USERNAME} \
    && useradd --uid ${USER_UID} --gid ${USER_GID} -m ${USERNAME} \
    && apt-get update \
    && apt-get install -y sudo \
    && echo ${USERNAME} ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/${USERNAME} \
    && chmod 0440 /etc/sudoers.d/${USERNAME}

ENV HOME /home/${USERNAME} 


# Enable bash history so it can be mounted and become persistent
RUN SNIPPET="export PROMPT_COMMAND='history -a' && export HISTFILE=/commandhistory/.bash_history" \
    && mkdir /commandhistory \
    && touch /commandhistory/.bash_history \
    && chown -R $USERNAME /commandhistory \
    && echo "${SNIPPET}" >> "/home/$USERNAME/.bashrc"

# ********************************************************
# * Anything else you want to do like clean up goes here *
# ********************************************************

# [Optional] Set the default user. Omit if you want to keep the default as root.
USER ${USERNAME}

RUN mkdir ${HOME}/init 
COPY .devcontainer/requirements.txt ${HOME}/init/requirements

RUN pip -q install pip --upgrade \
    && pip3 install -r ${HOME}/init/requirements

WORKDIR ${HOME}
