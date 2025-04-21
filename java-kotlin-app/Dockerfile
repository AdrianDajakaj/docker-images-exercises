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

# Gradle
ENV GRADLE_VERSION=8.7

RUN curl -fsSL https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -o gradle.zip && \
    unzip gradle.zip -d /opt/ && \
    ln -s /opt/gradle-${GRADLE_VERSION}/bin/gradle /usr/bin/gradle && \
    rm gradle.zip

ENV PATH="/opt/gradle-${GRADLE_VERSION}/bin:$PATH"

WORKDIR /app
COPY . .

# Build
RUN gradle build

# Run Hello
CMD ["gradle", "run", "--no-daemon"]
