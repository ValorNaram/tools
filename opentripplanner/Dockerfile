FROM openjdk:8-jre
LABEL maintainer="Malte Dölker" organization="Trufi Association e.V."

ARG OTP_VERSION="1.4.0"
ARG OTP_DOWNLOAD_URL="https://repo1.maven.org/maven2/org/opentripplanner/otp/${OTP_VERSION}/otp-${OTP_VERSION}-shaded.jar"

ENV JAVA_OPTS="-XX:+UnlockExperimentalVMOptions -XX:+UseCGroupMemoryLimitForHeap -XX:MaxRAMFraction=1"

RUN mkdir -p /opt/opentripplanner \
    && mkdir -p /var/otp \
    && curl -o /opt/opentripplanner/otp-shaded.jar ${OTP_DOWNLOAD_URL}

VOLUME /var/otp/graphs
WORKDIR /var/otp/graphs

EXPOSE 8080/tcp 8081/tcp

ENTRYPOINT [ "/bin/sh", "-c", "java ${JAVA_OPTS} -jar /opt/opentripplanner/otp-shaded.jar $0 $@" ]
