# 기본 이미지 선택
FROM ubuntu:latest

# 필요한 도구 설치
RUN apt-get update && apt-get install -y curl git unzip xz-utils zip libglu1-mesa openjdk-8-jdk wget clang cmake ninja-build pkg-config && \
    rm -rf /var/lib/apt/lists/*

# Flutter SDK 설치
RUN git clone https://github.com/flutter/flutter.git /usr/local/flutter
ENV PATH "$PATH:/usr/local/flutter/bin"
RUN flutter channel stable
RUN flutter upgrade
RUN flutter doctor

# Android SDK 설치
RUN wget https://dl.google.com/android/repository/commandlinetools-linux-7302050_latest.zip
RUN mkdir -p /usr/local/android-sdk/cmdline-tools
RUN unzip commandlinetools-linux-7302050_latest.zip -d /usr/local/android-sdk/cmdline-tools
RUN rm commandlinetools-linux-7302050_latest.zip
ENV PATH "$PATH:/usr/local/android-sdk/cmdline-tools/tools/bin:/usr/local/android-sdk/platform-tools"
RUN yes | sdkmanager --licenses
RUN sdkmanager "platform-tools" "platforms;android-30" "build-tools;30.0.3"
