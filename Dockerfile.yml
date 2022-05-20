#stage 1

FROM gradle:jdk11 as java_test

WORKDIR /home/gradle/src

COPY ./ ./

RUN gradle build --no-daemon
#because it's local not CI/CD
#stage 2

FROM openjdk:12-alpine


COPY --from=java_test /home/gradle/src/build/libs/*.jar ./
#from java_test copy /home/gradle copy everything with jar and create in /app/app.jar file

ENTRYPOINT ["java", "-jar", "app.jar"]
#app.jar  we must see it container we can see it with ls -ltr

#for example after COPY --from we must
#RUN ls -ltr 
