# github-actions-test

This repo uses GitHub Actions to run unit tests and build a Spring Boot JAR.

CI workflow: `.github/workflows/maven-ci.yml`
- Runs on push and PR
- JDK 17 (Temurin)
- Commands:
  - `mvn -B -ntp test` (with H2 profile active by `application.yml`)
  - `mvn -B -ntp -DskipTests package`
- Uploads `target/*.jar` as a build artifact

Local quickstart:
- Run tests: `mvn -B -ntp test`
- Package: `mvn -B -ntp -DskipTests package`
- Run app locally: `java -jar target/cicd-demo-0.0.1-SNAPSHOT.jar`
