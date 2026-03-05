# カスタムターミナル例（Python 事前インストール）

Showroom 用のカスタムターミナルイメージの例です。Python を事前にインストールしています。

## ビルド

```bash
podman build -t quay.io/<your-org>/showroom-terminal-python:latest .
```

## プッシュ

```bash
podman login quay.io
podman push quay.io/<your-org>/showroom-terminal-python:latest
```

## 使用

`helm/values.yaml` または `helm/components/showroom/values.yaml` で:

```yaml
showroom:
  terminal:
    image: "quay.io/<your-org>/showroom-terminal-python:latest"
```

## カスタマイズ

- 追加ツール: Dockerfile の `RUN dnf install -y` にパッケージを追加
- Python パッケージ: `pip install` を RUN に追加
