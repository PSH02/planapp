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
