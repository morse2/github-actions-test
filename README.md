# github-actions-test

This repo uses GitHub Actions to run unit tests and build a Spring Boot JAR.

CI workflow: `.github/workflows/maven-ci.yml`
- Runs on push and PR
- JDK 17 (Temurin)
- Commands:
  - `mvn -B -ntp test` (with H2 profile active by `application.yml`)
  - `mvn -B -ntp -DskipTests package`
- Uploads `target/*.jar` as a build artifact
- Also uploads test/coverage reports:
  - Surefire raw: `target/surefire-reports/`
  - Surefire HTML: `target/site/surefire-report.html` and `target/site/surefire-report/`
  - JaCoCo coverage HTML: `target/site/jacoco/index.html`

Local quickstart:
- Run tests: `mvn -B -ntp test`
- Generate HTML reports: `mvn -B -ntp org.apache.maven.plugins:maven-surefire-report-plugin:3.5.0:report-only org.jacoco:jacoco-maven-plugin:0.8.12:report`
- Package: `mvn -B -ntp -DskipTests package`
- Run app locally: `java -jar target/cicd-demo-0.0.1-SNAPSHOT.jar`

Download reports from Actions:
- After a workflow run completes, open the run page → Artifacts:
  - `test-reports-<run_number>`: contains `target/surefire-reports/`, `target/site/surefire-report/`, and `target/site/jacoco/`
  - `cicd-demo-jar-<run_number>`: packaged JAR


# Test it.
