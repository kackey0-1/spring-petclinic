# spring-petclinic Development Patterns

> Auto-generated skill from repository analysis

## Overview

The Spring Pet Clinic is a Java-based web application built with Spring Boot that demonstrates best practices for enterprise Java development. This codebase follows established patterns for dependency management, internationalization, database integration, and comprehensive testing. The project maintains both Maven and Gradle build configurations and supports multiple database backends with Docker containerization.

## Coding Conventions

### File Naming
- Use **camelCase** for all file names
- Test files follow pattern `*Tests.java` (e.g., `OwnerControllerTests.java`)
- Integration tests use `*IntegrationTests.java` pattern
- Properties files use lowercase with hyphens: `messages-en.properties`

### Import Organization
- Mixed import style allowing both wildcard and explicit imports
- Group imports by: Java standard library, Spring framework, third-party, project-specific
- Maintain consistent ordering within test and main source directories

### Commit Message Style
- Use freeform commit messages averaging 36 characters
- Common prefixes: `test:`, `feat:`
- Keep messages concise but descriptive
- Examples: `test: add owner validation tests`, `feat: upgrade spring boot to 2.7.0`

## Workflows

### Spring Boot Version Upgrade
**Trigger:** When upgrading Spring Boot to a new major or minor version  
**Command:** `/upgrade-spring-boot`

1. Update `build.gradle` with new Spring Boot version in plugins section
2. Update `pom.xml` parent version and dependency management
3. Review and update test files for API compatibility changes
4. Update `README.md` with new version requirements
5. Run full test suite to verify compatibility
6. Update any deprecated API usage found during testing

```gradle
// build.gradle example
plugins {
    id 'org.springframework.boot' version '3.1.0'
}
```

### Gradle Wrapper Upgrade
**Trigger:** When upgrading to a newer Gradle version  
**Command:** `/upgrade-gradle`

1. Update `gradle/wrapper/gradle-wrapper.properties` with new distributionUrl
2. Replace `gradle/wrapper/gradle-wrapper.jar` with new version binary
3. Update `gradlew` and `gradlew.bat` scripts if needed
4. Test build compatibility with `./gradlew build`
5. Update `build.gradle` configuration for new Gradle features if applicable

```properties
# gradle-wrapper.properties
distributionUrl=https\://services.gradle.org/distributions/gradle-8.0-bin.zip
```

### Maven Wrapper Upgrade
**Trigger:** When upgrading Maven to a newer version  
**Command:** `/upgrade-maven`

1. Update `.mvn/wrapper/maven-wrapper.properties` with new Maven version
2. Update `mvnw` and `mvnw.cmd` scripts for compatibility
3. Verify `pom.xml` works with new Maven version
4. Test build with `./mvnw clean install`
5. Update any Maven plugin versions if required

### Database Version Upgrade
**Trigger:** When upgrading MySQL, PostgreSQL, or other database versions  
**Command:** `/upgrade-databases`

1. Update `docker-compose.yml` with new database image versions
2. Update `k8s/db.yml` deployment with new container images
3. Modify integration test files (`MySqlIntegrationTests.java`, `MysqlTestApplication.java`)
4. Update connection configurations for new database features
5. Update `README.md` with new supported database versions
6. Test all database profiles to ensure compatibility

```yaml
# docker-compose.yml example
services:
  mysql:
    image: mysql:8.0
```

### Internationalization Enhancement
**Trigger:** When adding new translatable strings or updating existing translations  
**Command:** `/update-i18n`

1. Add or update base messages in `src/main/resources/messages/messages.properties`
2. Add corresponding translations to all language files:
   - `messages_en.properties`
   - `messages_es.properties`
   - `messages_fr.properties` (etc.)
3. Update HTML templates to use new message keys with `#{key}` syntax
4. Run `I18nPropertiesSyncTest.java` to verify translation completeness
5. Test UI in different locales to verify proper display

```properties
# messages.properties
welcome.message=Welcome to the Pet Clinic
owner.new=Add New Owner
```

```html
<!-- HTML template example -->
<h1 th:text="#{welcome.message}">Welcome</h1>
```

### README Documentation Update
**Trigger:** When project changes require documentation updates  
**Command:** `/update-readme`

1. Update version references throughout `README.md`
2. Correct any outdated installation or setup instructions
3. Fix typos and improve clarity of existing content
4. Add documentation for new features or configuration options
5. Verify all links and references are still valid
6. Update system requirements if they have changed

### Test Configuration Update
**Trigger:** When framework upgrades require test changes  
**Command:** `/update-tests`

1. Update integration test classes for new Spring Boot test annotations
2. Modify controller test classes for API changes
3. Update test configurations and application properties
4. Fix any deprecated test utilities or assertions
5. Ensure all test profiles still work correctly
6. Update mock configurations and test data setup

```java
// Example test update
@SpringBootTest
@AutoConfigureMockMvc
class OwnerControllerTests {
    @Test
    void shouldShowOwner() {
        // Updated test implementation
    }
}
```

## Testing Patterns

### Test File Organization
- Unit tests: `src/test/java/**/*Tests.java`
- Integration tests: `src/test/java/**/*IntegrationTests.java`
- Test application configurations: `*TestApplication.java`
- Use `@SpringBootTest` for integration tests
- Use `@WebMvcTest` for controller layer tests

### Database Testing
- Separate test profiles for different databases
- Integration tests extend base test classes
- Use test containers for database integration testing
- Mock external dependencies in unit tests

## Commands

| Command | Purpose |
|---------|---------|
| `/upgrade-spring-boot` | Upgrade Spring Boot version across build files and tests |
| `/upgrade-gradle` | Update Gradle wrapper and build configuration |
| `/upgrade-maven` | Update Maven wrapper version and configuration |
| `/upgrade-databases` | Update database versions in Docker and Kubernetes configs |
| `/update-i18n` | Add or update internationalization messages and translations |
| `/update-readme` | Update project documentation and fix formatting |
| `/update-tests` | Update test configurations for framework changes |