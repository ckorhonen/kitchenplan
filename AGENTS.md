# Working on Kitchenplan

This legacy Ruby CLI provisions macOS through Chef. `lib/` contains the CLI and
implementation, `bin/` the executable, `templates/` generated configuration, and
`test/` the tests. Preserve compatibility with the Gemfile/lockfile; historical CI
uses Ruby 2.0 and Bundler 1.x.

Use `bundle install` in an isolated compatible environment, then
`bundle exec rake test` (also the default task) for tests or
`bundle exec rake build` for the gem build. No separate lint/typecheck task is
defined. Inspect tests before running any that invoke provisioning.

Do not replay `.travis.yml` blindly: it installs the gem with sudo and runs
`kitchenplan setup` and `kitchenplan provision`, which alter the workstation.
Provisioning, system installation, and changes under `/opt` require explicit
scope and a disposable host; they are not ordinary local validation.

## Completing changes

Follow existing patterns and carry authorized work through the relevant checks,
repairing failures caused by the change. Choose routine implementation details
directly; ask only when missing information materially changes scope or outcome.
For documentation-only edits, check the diff, referenced paths, and command
accuracy rather than starting application runtimes. If a prerequisite blocks a
check, report the exact blocker and continue independent authorized work. Close
with changed paths, checks actually run and results, and remaining unverified
behavior; distinguish commands inspected from commands executed.
