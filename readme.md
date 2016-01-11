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
