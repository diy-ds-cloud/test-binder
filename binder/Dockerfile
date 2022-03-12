FROM jupyter/scipy-notebook:2fee7b754cbe AS base-python

USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        gpg zsh neovim curl build-essential

RUN curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | gpg --dearmor -o /usr/share/keyrings/githubcli-archive-keyring.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | tee /etc/apt/sources.list.d/github-cli.list > /dev/null && \
    apt-get update && \
    apt-get install -y gh

RUN git clone https://github.com/TheLocehiliosan/yadm.git /usr/local/share/yadm && \
    ln -s /usr/local/share/yadm/yadm /usr/local/bin/yadm

USER ${NB_USER}

# prevents complaints about group write permissions for ohmyzsh
ENV ZSH_DISABLE_COMPFIX=true
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended

ENV SHELL=/usr/bin/zsh