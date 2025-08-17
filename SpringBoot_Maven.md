# Maven in Spring Boot – Detailed Summary

## 1. Introduction
- Maven is not just a **build generation tool**, but a **project management tool**.
- Provides:
  - Build generation
  - Dependency resolution
  - Documentation
  - Standard project structure
- Uses **POM (Project Object Model)** to manage configurations.

---

## 2. Maven vs Ant
- **Ant (before Maven):**
  - Required instructions for both **what to do** and **how to do it**.
- **Maven:**
  - Requires only **what to do**.
  - Handles **how to do it** internally using plugins.

---

## 3. Project Structure (Spring Boot with Maven)
When creating a Spring Boot project with Maven:
- `src/main/java` → main application code.
- `src/test/java` → test cases.
- `pom.xml` → central configuration file.
- Package structure: `com.concept.coding.learning.springboot` (based on Group ID, Artifact ID).

---

## 4. Understanding `pom.xml`
### Key Elements:
1. **Schema Declaration**
   - Ensures POM follows Maven’s XML schema.

2. **Parent**
   - Defines inheritance from a parent POM.
   - If not explicitly defined → inherits from **Super POM**.

3. **Coordinates**
   - **Group ID**: Organization/Company (e.g., `com.concept.coding`).
   - **Artifact ID**: Project name (e.g., `learning-springboot`).
   - **Version**: Project version.

4. **Properties**
   - Key-value pairs for reusable configs.
   - Example:  
     ```xml
     <properties>
       <java.version>17</java.version>
     </properties>
     ```

5. **Repositories**
   - Defines remote sources for dependencies (e.g., Maven Central).
   - By default, Maven uses **Maven Central**.

6. **Dependencies**
   - External libraries required by the project.

7. **Build Element**
   - Allows adding **plugins** and **custom tasks** to lifecycle phases.

---

## 5. Maven Build Lifecycle
Maven defines **7 sequential phases**. Running a later phase executes all prior phases.

1. **Validate** → Checks project structure.
2. **Compile** → Converts source code to bytecode (`.class` files).
3. **Test** → Runs unit tests in `src/test/java`.
4. **Package** → Bundles compiled code into `.jar` or `.war`.
5. **Verify** → Runs additional checks (e.g., static code analysis via PMD/Checkstyle).
6. **Install** → Installs `.jar` into **local repository** (`~/.m2/repository`).
7. **Deploy** → Uploads package to **remote repository** (company repo or Maven Central).

---

## 6. Goals and Plugins
- Each phase has **default goals** (tasks).
- You can attach custom tasks via **plugins**.
- Example: Adding a **Checkstyle plugin** in `validate` phase:
  ```xml
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-checkstyle-plugin</artifactId>
        <executions>
          <execution>
            <phase>validate</phase>
            <goals>
              <goal>check</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
  ```

---

## 7. Local vs Remote Repository
- **Local Repository**: `~/.m2/repository` (stores downloaded dependencies and installed builds).
- **Remote Repository**:
  - Maven Central (default, public).
  - Company-specific repositories (secured, requires credentials).

**Settings:**
- `settings.xml` (inside `.m2/`) → configure local repo path, authentication, mirrors.

---

## 8. Deploying Artifacts
To deploy a `.jar` to remote repository:
- Add `distributionManagement` in `pom.xml`:
  ```xml
  <distributionManagement>
    <repository>
      <id>company-repo</id>
      <url>http://company.repo.url</url>
    </repository>
  </distributionManagement>
  ```
- Provide credentials in `settings.xml`:
  ```xml
  <servers>
    <server>
      <id>company-repo</id>
      <username>user</username>
      <password>pass</password>
    </server>
  </servers>
  ```

---

## 9. Commands Overview
- `mvn validate` → Validate project structure.
- `mvn compile` → Compile code to `.class` files (target/classes).
- `mvn test` → Run unit tests.
- `mvn package` → Create `.jar`/`.war` in `target/`.
- `mvn verify` → Run additional checks (e.g., PMD, static analysis).
- `mvn install` → Install artifact into local repository.
- `mvn deploy` → Deploy artifact to remote repository.

---

## 10. Key Takeaways
- Maven simplifies build and dependency management.
- Uses **convention over configuration** (standard project structure).
- Each project inherits from a **parent POM** (directly or via Super POM).
- Supports plugin-based extensibility for all lifecycle phases.
- Local repository speeds up dependency resolution.
- Deploying artifacts makes them reusable across teams/projects.

---
