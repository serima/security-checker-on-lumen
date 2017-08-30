# Example of using SensioLabs Security Advisories Checker

## TravisCI

### Found known vulnerabilities

https://travis-ci.org/serima/security-checker-on-lumen/builds/101483861

![travis-fail](http://snag.gy/lYmxc.jpg)

### Fixed known vulnerabilities

https://travis-ci.org/serima/security-checker-on-lumen/builds/101484312

![travis-fixed](http://snag.gy/x0ero.jpg)

```yaml
language: php
php:
  - 5.6

before_script:
  - composer self-update
  - composer install
  - chmod -R 777 storage

script:
  - vendor/bin/security-checker security:check
  - phpunit
```

## CircleCI

### Found known vulnerabilities

https://circleci.com/gh/serima/security-checker-on-lumen/7

![circle-fail](http://snag.gy/nC4cw.jpg)

### Fixed known vulnerabilities

https://circleci.com/gh/serima/security-checker-on-lumen/8

![circle-fixed](http://snag.gy/RZuFf.jpg)

#### CircleCI 1.0

```yaml
machine:
  timezone:
    Asia/Tokyo
  php:
    version: 5.6.14

test:
  override:
    - vendor/bin/security-checker security:check
    - vendor/bin/phpunit
```

#### CircleCI 2.0

```yaml
defaults: &defaults
  working_directory: ~/working_directory
  steps:
    - checkout
    - run: composer install -n --prefer-dist
    - run: vendor/bin/security-checker security:check
    - run: vendor/bin/phpunit

version: 2
jobs:
  build-php56:
    <<: *defaults
    docker:
      - image: circleci/php:5.6
  build-php70:
    <<: *defaults
    docker:
      - image: circleci/php:7.0

workflows:
  version: 2
  build:
    jobs:
      - build-php56
      - build-php70
```
