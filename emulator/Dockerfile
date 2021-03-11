FROM freeway/android:30.0.2

#inspired by Ivan Posokhov <posohof@gmail.com>
LABEL maintainer="a.zhilyaev73@gmail.com"

EXPOSE 22

ENV DEBIAN_FRONTEND noninteractive

# Install packages
RUN apt-get -qqy update && apt-get -qqy install --no-install-recommends \
    qemu-kvm \
    xvfb \
    ssh \
    openssh-server \
 && rm -rf /var/lib/apt/lists/*

RUN apt-get update && \
     apt-get install -yq --no-install-recommends \
     libasound2 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 \
     libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 \
     libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 \
     libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 \
     libnss3

# Installs Android SDK
RUN cd android && \
    yes | tools/bin/sdkmanager --licenses && \
    tools/bin/sdkmanager "emulator" "system-images;android-29;google_apis;x86_64" && \
    tools/bin/sdkmanager --update
