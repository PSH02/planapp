# 기본 이미지 선택
FROM ubuntu:latest

# 필요한 도구 설치
RUN apt-get update && apt-get install -y curl git unzip xz-utils zip libglu1-mesa openjdk-8-jdk wget

# Flutter SDK 설치
RUN git clone https://github.com/flutter/flutter.git /usr/local/flutter
ENV PATH "$PATH:/usr/local/flutter/bin"

# Flutter channel 설정 및 필요한 패키지 업데이트
RUN flutter channel stable
RUN flutter upgrade
RUN flutter doctor

# Android SDK 설치
RUN wget https://dl.google.com/android/repository/commandlinetools-linux-7302050_latest.zip
RUN mkdir -p /usr/local/android-sdk/cmdline-tools
RUN unzip commandlinetools-linux-7302050_latest.zip -d /usr/local/android-sdk/cmdline-tools
ENV PATH "$PATH:/usr/local/android-sdk/cmdline-tools/tools/bin"
RUN yes | sdkmanager --licenses
RUN sdkmanager "platform-tools" "platforms;android-30" "build-tools;30.0.3"
ENV PATH "$PATH:/usr/local/android-sdk/platform-tools"

# Linux toolchain 도구 설치
RUN apt-get install -y clang cmake ninja-build pkg-config
