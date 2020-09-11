# fakemail

A simple Bash script to redirect PHP mail requests to a local log file.

Created to work with Homebrew PHP installs.

# Install

```sh
brew tap jbylsma/fakemail
```

Configure all PHP versions with fakemail. This must be run manually whenever a
new PHP version is installed.

```sh
for dir in /usr/local/etc/php/*; do
  printf 'sendmail_path = /usr/local/bin/fakemail\n' >"${dir}/conf.d/fakemail.ini"
done
```
