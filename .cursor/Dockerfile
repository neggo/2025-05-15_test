FROM ubuntu:22.04

# 必要なパッケージのインストール
RUN apt-get update && apt-get install -y \
    curl \
    git \
    nodejs \
    npm \
    && rm -rf /var/lib/apt/lists/*

# Node.jsの設定
WORKDIR /app

# 注意: プロジェクトファイルはGitHubから直接クローンされるため、
# ここではCOPYコマンドは使用しません 