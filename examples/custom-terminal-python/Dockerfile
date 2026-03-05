# カスタムターミナルイメージ - Python 事前インストール版
# Showroom の terminal コンテナとして使用可能

FROM registry.access.redhat.com/ubi9/ubi:latest

# 必要なパッケージをインストール
RUN dnf install -y \
    bash \
    curl \
    python3 \
    python3-pip \
    && dnf clean all

# ttyd をインストール（7681 で待ち受け）
ARG TTYD_VERSION=1.7.4
RUN curl -fsSL "https://github.com/tsl0922/ttyd/releases/download/${TTYD_VERSION}/ttyd.x86_64" -o /usr/local/bin/ttyd \
    && chmod +x /usr/local/bin/ttyd

# lab-user 用（PVC でマウントされる）
RUN mkdir -p /home/lab-user && chown -R 1000:1000 /home/lab-user

USER 1000
WORKDIR /home/lab-user

EXPOSE 7681

# ttyd: -W で複数接続許可
CMD ["ttyd", "-W", "bash"]
