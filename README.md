# fakemail

A simple Bash script to redirect PHP mail requests to a local log file.

Designed to work with Homebrew PHP installs.

# Install

```sh
ln -s $(pwd)/fakemail /usr/local/bin/fakemail
```

All PHP versions must be configured to use fakemail. This must be run manually
whenever a new PHP version is installed.

```sh
for dir in /usr/local/etc/php/*; do
  printf 'sendmail_path = /usr/local/bin/fakemail\n' >"${dir}/conf.d/fakemail.ini"
done

brew services list |\
  awk '$1 ~ "^php@" && $2 == "started" { print $1; }' |\
  xargs -I{} brew services restart {}
```
