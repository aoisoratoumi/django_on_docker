# オフィシャルのalpineベースのpythonイメージをpull
FROM python:3.8.3-alpine

# ワークディレクトリーを設定
WORKDIR /usr/src/app

# 環境変数を設定
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONBUFFERED 1

# psycopg2の依存パッケージをインストール
RUN apk update && apk add \
    postgresql-dev \
    gcc \
    python3-dev \
    musl-dev \
    build-base \
    # wgetの依存パッケージをインストール
    openssl \
    # dev関係パッケージをインストール
    git \
    bash \
    sudo \
    py3-pip \
    # Pillowの依存パッケージをインストール
    jpeg-dev \
    zlib-dev \
    freetype-dev \
    lcms2-dev \
    openjpeg-dev \
    tiff-dev \
    tk-dev \
    tcl-dev \
    harfbuzz-dev \
    fribidi-dev

# 必要なpythonのパッケージをインストール
RUN pip install --upgrade pip
COPY ./requirements.txt .
RUN pip install -r requirements.txt

# entrypoint.shをコピー
COPY ./entrypoint.sh .

# プロジェクトをコピー
COPY . .

# run entrypoint.sh
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]