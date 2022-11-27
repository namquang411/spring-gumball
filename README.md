# spring-gumball

# Part 1 CI-Workflow

1. Change gradle.yml
```java
# This workflow will build a Java project with Gradle
# See Also: https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-java-with-gradle

name: Java CI with Gradle

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    # The checkout step downloads a copy of your repository on the runner.
    - uses: actions/checkout@v3

    # The setup-java step configures the Java 11 JDK by Adoptium.
    - name: Set up JDK 11
      uses: actions/setup-java@v3
      with:
        java-version: '11'
        distribution: 'temurin'

    # Make sure gradle wrapper is executable
    - name: Grant execute permission for gradlew
      run: chmod +x gradlew

    # The "Build with Gradle" step does a build using the gradle/gradle-build-action 
    # action provided by the Gradle organization on GitHub. The action takes care of 
    # invoking Gradle, collecting results, and caching state between jobs. 
    # For more information, See: https://github.com/gradle/gradle-build-action.      
    - name: Build with Gradle
      run: ./gradlew build

    # List the Build output folder to confirm JAR file was built
    - name: Build Result
      run: ls build/libs

    # Gradle will usually create output files like JARs, EARs, or WARs in the build/libs directory. 
    # You can upload the contents of that directory using the upload-artifact action.
    # See: https://docs.github.com/en/actions/using-workflows/storing-workflow-data-as-artifacts
    - name: Upload a Build Artifact
      uses: actions/upload-artifact@v3.1.1
      with:
        name: spring-gumball
        path: build/libs/spring-gumball-2.0.jar
```
2. Result

![gradle](https://github.com/namquang411/spring-gumball/image/gradle-action.png)


# Part 2 CD-Workflow

1. Create Cluster

![cluster](https://github.com/namquang411/spring-gumball/image/cluster.png)

2. Confirm API work

![api](https://github.com/namquang411/spring-gumball/image/api-ready.png)

3. Dashboard - Project ID

![dashboard](https://github.com/namquang411/spring-gumball/image/dashboard.png)

4. Create Service acc

![service](https://github.com/namquang411/spring-gumball/image/service-acc.png)

5. Success create service

![suc](https://github.com/namquang411/spring-gumball/image/success-service.png)

6. Add grant access

![add](https://github.com/namquang411/spring-gumball/image/access.png)

7. Success add access

![suc-add](https://github.com/namquang411/spring-gumball/image/success-add.png)

8. New-Key

![new](https://github.com/namquang411/spring-gumball/image/new-key.png)

9. Download key

![down](https://github.com/namquang411/spring-gumball/image/downloaded.png)

10. Key

![key](https://github.com/namquang411/spring-gumball/image/key.png)

11. Create secret GKE

![gke](https://github.com/namquang411/spring-gumball/image/gke.png)

12. Create Release

![rel](https://github.com/namquang411/spring-gumball/image/realease.png)

13. Success Release

![suc-re](https://github.com/namquang411/spring-gumball/image/suc-rel.png)

14. Complete Release - 2.0 I put wrong code in google.yml, then I fix it and this one is running success

![com](https://github.com/namquang411/spring-gumball/image/complete-release.png)

15. Workloads

![work](https://github.com/namquang411/spring-gumball/image/workload.png)

16. Service

![service](https://github.com/namquang411/spring-gumball/image/service.png)

17. Create Ingress

![ingress](https://github.com/namquang411/spring-gumball/image/ingress.png)

18. GKE worked

![finish](https://github.com/namquang411/spring-gumball/image/finished.png)