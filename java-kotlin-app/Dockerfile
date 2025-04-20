FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

# Updates + Java 8 + other tools
RUN apt-get update && apt-get install -y \
    openjdk-8-jdk \
    curl \
    git \
    unzip \
    zip \
    && apt-get clean

# Kotlin
RUN curl -s https://get.sdkman.io | bash && \
    bash -c "source $HOME/.sdkman/bin/sdkman-init.sh && sdk install kotlin"

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH="$PATH:/root/.sdkman/candidates/kotlin/current/bin"


CMD ["java", "-version"]
