FROM openjdk:17-jdk-slim

WORKDIR /app

# Gradle 설치
RUN apt-get update && apt-get install -y wget unzip && \
    wget https://services.gradle.org/distributions/gradle-8.3-bin.zip -P /tmp && \
    unzip -d /opt/gradle /tmp/gradle-8.3-bin.zip && \
    ln -s /opt/gradle/gradle-8.3/bin/gradle /usr/bin/gradle

# 전체 소스 복사
COPY . .

# 의존성 빌드
RUN gradle build -x test --no-daemon

# Spring Boot 포트
EXPOSE 8080

# 애플리케이션 실행
CMD ["gradle", "bootRun"]
