# Changelog

This changelog is used to track all major changes to django_apscheduler.

## v0.4.0 (UNRELEASED)

**Enhancements**

- Drop support for Python 2.7, convert codebase to Python 3.6+.
- CI: drop coverage for Python 2.7 and Django <= 2.1, which are no longer maintained upstream.
- CI: add coverage for Python 3.7 and 3.8, as well as Django long term support (LTS) and the latest released versions.
- CI: un-pin dependency on agronholm/apscheduler#149, which has since been merged and released upstream.
- Rename Django `test_settings.py` file to prevent collision with actual test scripts.
- Clean up unused dependencies / update dependencies to latest available versions.
- Switch to Black code formatting.
- Align package layout with official [Django recommendations](https://docs.djangoproject.com/en/dev/intro/reusable-apps/#packaging-your-app)
- Move UI-related DjangoJobExecution.html_status out of model definition and in to the associated model admin definition.
- Add `help_text` to model fields to document their use.
- Remove unused code fragments.
- Add Python type annotations.
- Implement various Django best practices for QuerySet management and model instance creation / updates.
- Drop `DjangoJob.name` field in favor of aligning with using APScheduler's `id` field. NOTE: please run your Django
  migrations again - might take a while depending on the number of `DjangoJobExecutions` in your database.
- Acquire a DB lock when updating `DjangoJob` or `DjangoJobExecution` instances. This should be safer for multi-threaded
  usage.
- Switch to using `BigAutoField` for `DjangoJobExecution`'s primary keys. This should prevent running out of usable
  ID's for deployments with a very large number of job executions in the database (Resolves [#36](https://github.com/jarekwg/django-apscheduler/issues/36)). 

**Fixes**

- Fix PEP8 code formatting violations.