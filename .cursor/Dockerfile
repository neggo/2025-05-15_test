FROM ubuntu:22.04

# タイムゾーンの設定
ENV TZ=Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 基本的な開発ツールのインストール
RUN apt-get update && apt-get install -y \
    curl \
    git \
    build-essential \
    ca-certificates \
    gnupg \
    wget \
    vim \
    nano \
    tmux \
    zsh \
    python3 \
    python3-pip \
    sudo \
    ssh \
    less \
    htop \
    net-tools \
    lsof \
    && rm -rf /var/lib/apt/lists/*

# Node.jsの最新LTSバージョンをインストール
RUN mkdir -p /etc/apt/keyrings
RUN curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
RUN echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_20.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list
RUN apt-get update && apt-get install -y nodejs && rm -rf /var/lib/apt/lists/*

# 開発用Node.jsツールのインストール
RUN npm install -g npm@latest \
    nodemon \
    typescript \
    ts-node \
    eslint \
    prettier

# Git設定
RUN git config --system core.editor "vim" && \
    git config --system core.fileMode false

# Oh My Zsh のインストール
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended

# 作業ディレクトリの設定
WORKDIR /app

# Node.jsのグローバル設定
ENV NODE_ENV=development

# システムの制限を緩和
RUN ulimit -n 65535 || true

# デフォルトシェルをzshに変更
SHELL ["/bin/zsh", "-c"]

# 注意: プロジェクトファイルはGitHubから直接クローンされるため、
# ここではCOPYコマンドは使用しません 