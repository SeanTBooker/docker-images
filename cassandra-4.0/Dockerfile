FROM openjdk:8u252-slim


ARG STARGATE_VERSION=v1.0.7


RUN apt update -qq \
    && apt install curl unzip iproute2 libaio1 -y \
    && apt autoremove --yes \
    && apt clean all \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sL https://github.com/stargate/stargate/releases/download/${STARGATE_VERSION}/stargate-jars.zip > stargate-jars.zip \
    && unzip stargate-jars -x "*/persistence-*" \
    && unzip stargate-jars "*/persistence-api*" \
    && unzip stargate-jars "*/persistence-cassandra-4.0*" \
    && rm stargate-jars.zip

RUN chmod +x starctl
ENTRYPOINT ["./starctl"]
