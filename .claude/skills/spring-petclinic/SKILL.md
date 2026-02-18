# spring-petclinic Development Patterns

> Auto-generated skill from repository analysis

## Overview

The Spring Pet Clinic is a sample Spring Boot application that demonstrates best practices for Java web development. This codebase follows established patterns for framework upgrades, internationalization, documentation maintenance, and build configuration management. The project serves as a reference implementation for Spring Boot applications with comprehensive testing and multi-language support.

## Coding Conventions

### File Naming
- Use **camelCase** for all file names
- Test files follow the pattern `*Tests.java` (e.g., `PetClinicApplicationTests.java`)
- Configuration files use kebab-case (e.g., `docker-compose.yml`)

### Import Style
- Mixed import organization depending on file context
- Group imports by package hierarchy
- Separate third-party imports from internal imports

### Commit Messages
- Use freeform style with descriptive messages
- Common prefixes: `test:`, `feat:`
- Keep messages concise (average ~36 characters)
- Focus on what changed rather than how

## Workflows

### Spring Boot Version Upgrade
**Trigger:** When upgrading to a new Spring Boot release
**Command:** `/upgrade-spring-boot`

1. Update the Spring Boot version in `build.gradle`
2. Update the corresponding version in `pom.xml`
3. Review and update test files for compatibility changes in `src/test/java/**/*Tests.java`
4. Update application configuration files if breaking changes exist
5. Run full test suite to ensure compatibility
6. Update README.md if version requirements changed

### Gradle Version Upgrade
**Trigger:** When updating build tooling
**Command:** `/upgrade-gradle`

1. Update `gradle/wrapper/gradle-wrapper.properties` with new Gradle version
2. Download and replace `gradle/wrapper/gradle-wrapper.jar`
3. Update `gradlew` and `gradlew.bat` scripts if necessary
4. Review `build.gradle` for deprecated syntax or new features
5. Test build process on multiple platforms

### Maven Version Upgrade
**Trigger:** When updating Maven wrapper
**Command:** `/upgrade-maven`

1. Update version in `.mvn/wrapper/maven-wrapper.properties`
2. Update `mvnw` and `mvnw.cmd` scripts if needed
3. Test Maven build process
4. Verify wrapper downloads correct version

### README Documentation Updates
**Trigger:** When fixing documentation issues or clarifying project setup
**Command:** `/update-docs`

1. Review current `README.md` for accuracy
2. Fix any version mismatches with actual dependencies
3. Clarify setup and usage instructions
4. Polish markdown formatting and structure
5. Ensure all links are functional
6. Update prerequisites and system requirements

### Database Version Upgrade
**Trigger:** When updating database dependencies
**Command:** `/upgrade-database`

1. Update database image versions in `docker-compose.yml`
2. Update Kubernetes database configuration in `k8s/db.yml`
3. Modify integration test configurations in `src/test/java/**/My*IntegrationTests.java`
4. Update `README.md` with new database version requirements
5. Test database connectivity and schema compatibility

### Internationalization Enhancement
**Trigger:** When adding new translatable strings or updating existing ones
**Command:** `/update-i18n`

1. Add or update base messages in `src/main/resources/messages/messages.properties`
2. Update all language-specific files (`messages_*.properties`)
3. Update HTML templates in `src/main/resources/templates/**/*.html` with message keys
4. Ensure consistent key naming across all language files
5. Test UI with different language settings

### Copyright Year Update
**Trigger:** At the beginning of each year
**Command:** `/update-copyright`

1. Update copyright headers in all Java source files in `src/main/java/**/*.java`
2. Update copyright headers in test files in `src/test/java/**/*.java`
3. Use consistent copyright format across all files
4. Automate with find/replace for efficiency

### Build Configuration Cleanup
**Trigger:** When maintaining build scripts and dependencies
**Command:** `/cleanup-build`

1. Review and clean up `build.gradle` dependencies
2. Update `pom.xml` with current best practices
3. Remove outdated or unused configurations
4. Standardize formatting and organization
5. Update plugin versions to latest stable releases

## Testing Patterns

### Test File Organization
- Test files end with `Tests.java` suffix
- Integration tests follow pattern `My*IntegrationTests.java`
- Tests are located in `src/test/java/` mirroring main source structure

### Test Categories
- Unit tests for individual components
- Integration tests for database and external service interactions
- Web layer tests for controller functionality

## Commands

| Command | Purpose |
|---------|---------|
| `/upgrade-spring-boot` | Upgrade Spring Boot framework to newer version |
| `/upgrade-gradle` | Upgrade Gradle build tool version |
| `/upgrade-maven` | Upgrade Maven wrapper version |
| `/update-docs` | Update README and project documentation |
| `/upgrade-database` | Upgrade database versions in Docker and configs |
| `/update-i18n` | Add or update internationalization messages |
| `/update-copyright` | Update copyright year in all source files |
| `/cleanup-build` | Clean up and update build configuration files |