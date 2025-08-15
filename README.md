# TASK 8: Run a Simple Java Maven Build Job in Jenkins

## Objective
Learn how to use Jenkins to build a simple Java application using Maven .

---

## Tools Required (All Free)
- **Jenkins** (installed locally)
- **Java JDK** 8 
- **Maven**
- **Git** (optional — can run from a local folder)

---

## Deliverables
- ✅ A basic Java **HelloWorld** app (with `pom.xml`)
- ✅ Jenkins Freestyle job configured to build it
- ✅ Screenshot of successful build console output

---

## Sample Dataset/Repo
**Repo name:** `hello-java-maven`  
**Contents:**
- `src/main/java/HelloWorld.java`
- `pom.xml`

---

## Step-by-Step Guide

### 1️ Create Java App
Create a Java file at the specified path:

**`src/main/java/HelloWorld.java`**
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}
```
### 2 Create pom.xml File
Create a pom.xml file in the root of your project directory.
```XML
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>hello</artifactId>
    <version>1.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
            </plugin>
        </plugins>
    </build>
</project>
```
### 3 Configure Jenkins
* Open Jenkins in your browser, typically at http://localhost:8080.

* Navigate to Manage Jenkins → Global Tool Configuration.

* Scroll down to the Maven section and click Add Maven.

    - Name: Maven 3.8.6 (or your preferred version)

    - nable Install automatically.

    - Select a version from the dropdown.

    - Click Save.

* Go back to the Jenkins dashboard and click New Item.

    - Enter an item name (e.g., hello-java-maven-build).

    - Select Freestyle project and click OK.

* In the project configuration page, scroll down to the Build Steps section.

    - Click Add build step and select Invoke top-level Maven targets.

    - Maven Version: Select the Maven version you configured earlier.

    - Goals: clean package

* Click Save to finish creating the job.

* Click Build Now from the job's main page to run it.
  ### 4 Verify Build
* In the Build History panel on the left, click on the build number (e.g., #1).

* Select Console Output to view the build logs.

* Look for the BUILD SUCCESS message at the end of the log.
  ---
  ###  Expected Output
  When successful, the Maven build will compile and package the Java application. The console will display the output from the application and confirm the build's success.

```log
 Started by user admin
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/Task-8
[WS-CLEANUP] Deleting project workspace...
[WS-CLEANUP] Deferred wipeout is used...
[WS-CLEANUP] Done
The recommended git tool is: NONE
No credentials specified
Cloning the remote Git repository
Cloning repository https://github.com/yogeshpenumur/hello-java-maven-task-8
 > git init /var/lib/jenkins/workspace/Task-8 # timeout=10
Fetching upstream changes from https://github.com/yogeshpenumur/hello-java-maven-task-8
 > git --version # timeout=10
 > git --version # 'git version 2.43.0'
 > git fetch --tags --force --progress -- https://github.com/yogeshpenumur/hello-java-maven-task-8 +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git config remote.origin.url https://github.com/yogeshpenumur/hello-java-maven-task-8 # timeout=10
 > git config --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/* # timeout=10
Avoid second fetch
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision da33079822f43a395c0150e7c05ccd6c5cfd8af7 (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f da33079822f43a395c0150e7c05ccd6c5cfd8af7 # timeout=10
Commit message: "src_commit"
 > git rev-list --no-walk da33079822f43a395c0150e7c05ccd6c5cfd8af7 # timeout=10
[Task-8] $ /var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/Maven/bin/mvn -f pom.xml clean install
[INFO] Scanning for projects...
[INFO] 
[INFO] -------------------------< com.example:hello >--------------------------
[INFO] Building hello 1.0
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- clean:3.2.0:clean (default-clean) @ hello ---
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ hello ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /var/lib/jenkins/workspace/Task-8/src/main/resources
[INFO] 
[INFO] --- compiler:3.8.1:compile (default-compile) @ hello ---
[INFO] No sources to compile
[INFO] 
[INFO] --- resources:3.3.1:testResources (default-testResources) @ hello ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /var/lib/jenkins/workspace/Task-8/src/test/resources
[INFO] 
[INFO] --- compiler:3.8.1:testCompile (default-testCompile) @ hello ---
[INFO] No sources to compile
[INFO] 
[INFO] --- surefire:3.2.5:test (default-test) @ hello ---
[INFO] No tests to run.
[INFO] 
[INFO] --- jar:3.4.1:jar (default-jar) @ hello ---
[WARNING] JAR will be empty - no content was marked for inclusion!
[INFO] Building jar: /var/lib/jenkins/workspace/Task-8/target/hello-1.0.jar
[INFO] 
[INFO] --- install:3.1.2:install (default-install) @ hello ---
[INFO] Installing /var/lib/jenkins/workspace/Task-8/pom.xml to /var/lib/jenkins/.m2/repository/com/example/hello/1.0/hello-1.0.pom
[INFO] Installing /var/lib/jenkins/workspace/Task-8/target/hello-1.0.jar to /var/lib/jenkins/.m2/repository/com/example/hello/1.0/hello-1.0.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.263 s
[INFO] Finished at: 2025-08-15T11:17:21+05:30
[INFO] ------------------------------------------------------------------------
Archiving artifacts
Finished: SUCCESS
```

