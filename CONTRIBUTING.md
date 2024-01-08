# Contributing

When contributing to diKTat, it is important to follow the project's [Code of Conduct](CODE_OF_CONDUCT.md).

## Requirements

- Java 11

## Steps to Contribute

1. Fork the main repository to your GitHub account. You will need to enable GitHub Actions workflows if you want to run
   all workflows on your fork.
2. Create a new branch to accommodate your changes
3. Make your changes and verify that the tests pass:
   1. Run all the tests:
      ```shell
      ./gradlew test
      ```
   2. Or run the tests only for the subproject you changed. For example:
      ```shell
      ./gradlew :diktat-gradle-plugin:test
      ```
   3. Commit and push the changes to see GitHub Actions workflows' results.
4. Submit a pull request
5. Participate in the code review process by responding to feedback

## Technical details

The main components are:

| Name                   | Description                                                                                                                                     |
|:-----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------|
| `diktat-rules`         | Rules that diKTat supports out of the box                                                                                                       |
| `diktat-common-test`   | Util methods for functional/unit tests that can be used for running your code fixer on the initial code and compare it with the expected result |
| `diktat-gradle-plugin` | The code for diKTat Gradle plugin                                                                                                               |
| `diktat-maven-plugin`  | The code for diKTat Maven plugin                                                                                                                |

Mainly, we wanted to create a common configurable mechanism that
will give us a chance to enable/disable and customize all rules.

That's why we added logic for:

1. Parsing `.yml` file with configurations of rules and passing it to visitors;
2. Passing information about properties to visitors.
   This information is handy when you are trying to get, for example, a filename of file where the code is stored;
3. We added a bunch of visitors, checkers and fixers that will extend KTlint functionality with code style rules;
4. We have proposed a code style for Kotlin language.

Before you make a pull request, make sure the build is clean as we have a lot of tests and another pre-checks:

```bash
./gradlew clean build
```

## git hooks

The project contains some hooks to a commit messages:

1. Your commit message should have the following format:
    ```
    Brief Description

    ### What's done:
    1. Long description
    2. Long description
    ```
2. Please also remember to update documentation on Wiki after the merge approval and before merge.
