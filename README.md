This project purpose is so developers who need quick access to Unit testing
tools can have an approach to easily do so using Lando.

## Before starting
It is worth mentioning that this little project presumes default landoconfiguration
is in place, extra work might be done to adapt this repo to some local setups.

## Install
To start on a fresh Vanilla Drupal 9 site. Do the following:

1. Create a Drupal 9 project locally and clone this repo files into your project root:
``` sh
composer create-project drupal/recommended-project d9phpunit
cd d9phpunit
git clone git@github.com:fourkitchens/lando-d9phpunit.git
mv lando-d9phpunit/.* .
mv lando-d9phpunit/* .
rm -rf lando-d9phpunit
```
You should end up with the files found in this repo at the root of your project.

2. With composer, install development tools:
`composer require drupal/core-dev --dev --with-all-dependencies && composer require --dev phpspec/prophecy-phpunit`
3. Make directories for browser output, which will help debug Functional tests:
`mkdir web/sites/simpletest && mkdir web/sites/simpletest/browser_output`
4. Run `lando start` to get your local environment setup and running.
5. Start testing with `lando test`, (e.g. `lando test --verbose --debug --stop-on-failure  web/core/modules/action/tests/src/FunctionalJavascript/ActionFormAjaxTest.php`)

## Notes
- If deprecations are getting in your way, uncomment the `phpunit.xml` env var
`SYMFONY_DEPRECATIONS_HELPER` which is set to `disabled`.

## References
This was based on this very cool article: https://agile.coop/blog/drupal-phpunit-tests-lando/.
