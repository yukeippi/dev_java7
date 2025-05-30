FROM debian:bullseye

# デフォルトシェルをbashに設定
SHELL ["/bin/bash", "-c"]

# 必要なパッケージのインストール
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    unzip \
    bash \
    readline-common \
    libreadline-dev \
    && rm -rf /var/lib/apt/lists/*

# シェルの設定
RUN echo "set -o vi" > /etc/profile.d/bash_history.sh && \
    echo "export HISTCONTROL=ignoreboth:erasedups" >> /etc/profile.d/bash_history.sh && \
    echo "export HISTSIZE=10000" >> /etc/profile.d/bash_history.sh && \
    echo "export HISTFILESIZE=10000" >> /etc/profile.d/bash_history.sh && \
    echo "shopt -s histappend" >> /etc/profile.d/bash_history.sh && \
    chmod +x /etc/profile.d/bash_history.sh

# inputrcの設定
RUN echo '"\e[A": history-search-backward' > /etc/inputrc && \
    echo '"\e[B": history-search-forward' >> /etc/inputrc && \
    echo 'set show-all-if-ambiguous on' >> /etc/inputrc && \
    echo 'set completion-ignore-case on' >> /etc/inputrc

# OpenJDK 7のインストール
RUN mkdir -p /opt/java && \
    curl -L https://download.java.net/openjdk/jdk7u75/ri/jdk_ri-7u75-b13-linux-x64-18_dec_2014.tar.gz | \
    tar -xz -C /opt/java && \
    ln -s /opt/java/java-se-7u75-ri /opt/java/jdk7

# Maven 3.2.5のインストール（Java 7/8と互換性のあるバージョン）
RUN mkdir -p /usr/share/maven \
    && curl -fsSL https://archive.apache.org/dist/maven/maven-3/3.2.5/binaries/apache-maven-3.2.5-bin.tar.gz \
    | tar -xzC /usr/share/maven --strip-components=1 \
    && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

# 環境変数の設定
ENV MAVEN_HOME=/usr/share/maven
ENV JAVA_HOME=/opt/java/jdk7
ENV PATH=$JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH

# vscodeユーザーの作成（デフォルトシェルをbashに設定）
RUN groupadd --gid 1000 vscode \
    && useradd --uid 1000 --gid 1000 -m vscode -s /bin/bash \
    && apt-get update \
    && apt-get install -y sudo \
    && echo vscode ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/vscode \
    && chmod 0440 /etc/sudoers.d/vscode \
    && rm -rf /var/lib/apt/lists/*

# 作業ディレクトリの設定
WORKDIR /workspace

# vscodeユーザーがJava 7とMavenを使用できるように権限を設定
RUN chown -R 1000:1000 /opt/java && \
    chmod -R a+r /opt/java && \
    find /opt/java -type d -exec chmod a+x {} \;
