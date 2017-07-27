FROM ubuntu:16.04

RUN apt-get update && apt-get install --no-install-recommends -y openjdk-8-jdk-headless wget unzip

RUN mkdir -p /opt/android && cd /opt/android; \
	wget https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip -O sdktools.zip && \
	unzip sdktools.zip && \
	rm sdktools.zip

ENV ANDROID_HOME /opt/android

ENV PATH ${PATH}:${ANDROID_HOME}/tools/bin:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools

RUN mkdir -p ${ANDROID_HOME}/licenses/ && \
	echo "8933bad161af4178b1185d1a37fbf41ea5269c55" > ${ANDROID_HOME}/licenses/android-sdk-license && \
	echo "84831b9409646a918e30573bab4c9c91346d8abd" > ${ANDROID_HOME}/licenses/android-sdk-preview-license && \
	mkdir -p ~/.android && \
	echo "count=0" > ~/.android/repositories.cfg

RUN sdkmanager 'ndk-bundle' 'platforms;android-26' 'build-tools;26.0.1'

RUN mkdir -p /opt/workspace
WORKDIR /opt/workspace

