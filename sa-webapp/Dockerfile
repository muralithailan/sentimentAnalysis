FROM maven:3.5-jdk-8 as builder

WORKDIR /usr/src

COPY . .

RUN  mvn package && \
    cp target/sentiment*.jar target/app.jar



FROM openjdk:8-jdk-alpine
# Environment Variable that defines the endpoint of sentiment-analysis python api.
ENV SA_LOGIC_API_URL http://localhost:5000

WORKDIR /home/user

COPY --from=builder /usr/src/target/app.jar .
#ADD target/sentiment-analysis-web-0.0.1-SNAPSHOT.jar /
EXPOSE 8080

CMD ["java", "-jar", "/home/user/app.jar", "--sa.logic.api.url=${SA_LOGIC_API_URL}"]