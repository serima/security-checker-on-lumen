# Example of using SensioLabs Security Advisories Checker

## TravisCI

### Found known vulnerabilities

https://travis-ci.org/serima/security-checker-on-lumen/builds/101483861

### Fixed known vulnerabilities

https://travis-ci.org/serima/security-checker-on-lumen/builds/101484312

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

### Fixed known vulnerabilities

https://circleci.com/gh/serima/security-checker-on-lumen/8

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
