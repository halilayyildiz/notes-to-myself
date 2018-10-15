FROM alpine/git as clone
ARG url
RUN mkdir /root/.ssh/
COPY id_rsa /root/.ssh/
RUN ssh-keyscan -H code.siemens.com >> /root/.ssh/known_hosts
RUN chmod 400 /root/.ssh/id_rsa
WORKDIR /app
RUN git clone ${url}
RUN rm /root/.ssh/id_rsa

FROM maven:3.5.4-jdk-8 as build
ARG project 
WORKDIR /app
COPY --from=clone /app/noms/code/${project} /app
COPY settings.xml /root/.m2/settings.xml
RUN mvn package

FROM openjdk:8-jre-alpine
ARG artifactid
ARG version
ENV artifact ${artifactid}-${version}.jar
WORKDIR /app
COPY --from=build /app/target/${artifact} /app
EXPOSE 8080
ENTRYPOINT ["sh", "-c"]
CMD ["java -jar ${artifact}"]
