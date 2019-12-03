FROM reactnativecommunity/react-native-android:latest


RUN apt update -y
RUN apt install -y lib32stdc++6 

ENV PUB_HOSTED_URL="https://pub.flutter-io.cn"
ENV FLUTTER_STORAGE_BASE_URL="https://storage.flutter-io.cn"
ENV FLUTTER_VERSION="v1.9.1+hotfix.6"
# Install Flutter.
ENV FLUTTER_ROOT="/opt/flutter"
RUN git clone --branch $FLUTTER_VERSION --depth=1 https://github.com/flutter/flutter "${FLUTTER_ROOT}"
ENV PATH="${FLUTTER_ROOT}/bin:${PATH}"

# Disable analytics and crash reporting on the builder.
RUN flutter config  --no-analytics

# Perform an artifact precache so that no extra assets need to be downloaded on demand.
RUN flutter precache

# Accept licenses.
RUN yes "y" | flutter doctor --android-licenses

# Perform a doctor run.
RUN flutter doctor -v

ENV PATH $PATH:/flutter/bin/cache/dart-sdk/bin:/flutter/bin

CMD ['ansible']

# Flutter
#RUN wget https://github.com/flutter/flutter/archive/v1.9.1+hotfix.6.tar.gz
#RUN tar -zxvf v1.9.1+hotfix.6.tar.gz 
#RUN rm v1.9.1+hotfix.6.tar.gz
#RUN git clone -b stable https://github.com/flutter/flutter.git
#ENV PATH="/flutter/bin:${PATH}"
#RUN flutter doctor
# RUN flutter config --no-analytics
# RUN apt-get update
# RUN apt install lib32stdc++6
#RUN sysctl -w fs.inotify.max_user_watches="99999999"
# Set a useful default shell
#ENV SHELL /bin/bash

