# Example Gradle Project

This project is used for demonstration of [yamory](https://yamory.io).
Please enjoy hunting vulns!

## Requirements

- Java 17+
- Gradle 9.6+

## Commands

### Check Gradle version and project structure

```sh
./gradlew --version --console=plain --no-daemon
./gradlew projects --console=plain --no-daemon
```

### Print dependency trees

```sh
./gradlew \
  :dependencies \
  :subproject-db:dependencies \
  :subproject-dir:dependencies \
  :subproject-dir:modules1:dependencies \
  :subproject-dir:modules1:nested-subproject1:dependencies \
  :subproject-dir:modules1:nested-subproject2:dependencies \
  :subproject-dir:modules2:dependencies \
  :subproject-dir:modules2:nested-subproject1:dependencies \
  :subproject-dir:modules2:nested-subproject2:dependencies \
  :subproject-dir:modules2:nested-subproject3:dependencies \
  :subproject-util:dependencies \
  :subproject-web:dependencies \
  --console=plain --no-daemon --no-parallel
```

### List subproject directories via init script

```sh
./gradlew --init-script ./scripts/yamory-subproject-dirs.gradle \
  --console=plain --no-daemon -q help --no-configuration-cache
```

### Run from a single subproject (e.g. `subproject-util`)

```sh
cd subproject-util
./gradlew dependencies
./gradlew --init-script ../scripts/yamory-subproject-dirs.gradle \
  --console=plain --no-daemon -q help --no-configuration-cache
./gradlew projects --console=plain --no-daemon
```
