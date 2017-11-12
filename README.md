# Basic Intro
<a href="https://github.com/DennyZhang?tab=followers"><img align="right" width="200" height="183" src="https://raw.githubusercontent.com/USDevOps/mywechat-slack-group/master/images/fork_github.png" /></a>

[![Build Status](https://travis-ci.org/DennyZhang/detect_suspicious_process.svg?branch=master)](https://travis-ci.org/DennyZhang/detect_suspicious_process) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

[![LinkedIn](https://raw.githubusercontent.com/USDevOps/mywechat-slack-group/master/images/linkedin.png)](https://www.linkedin.com/in/dennyzhang001) [![Slack](https://raw.githubusercontent.com/USDevOps/mywechat-slack-group/master/images/slack.png)](https://www.dennyzhang.com/slack) [![Github](https://raw.githubusercontent.com/USDevOps/mywechat-slack-group/master/images/github.png)](https://github.com/DennyZhang)

File me [tickets](https://github.com/DennyZhang/detect_suspicious_process/issues) or star [the repo](https://github.com/DennyZhang/detect_suspicious_process).

Read more: https://www.dennyzhang.com/suspicious_process

Scan all OS processes. Check them against a whitelist.

Any processes not in the list is supposed to be **suspicious**.

# How To Use
```
git clone https://github.com/DennyZhang/detect_suspicious_process.git
cd detect_suspicious_process
```

```
# Prepare a whilelist. Each line is a regexp
cat > /tmp/whitelist.txt << EOF
/sbin/getty -.*
dbus-daemon .*
 acpid -c /etc/acpi/events -s /var/run/acpid.socket$
 atd$
 cron$
 /lib/systemd/systemd-udevd --daemon$
 /lib/systemd/systemd-logind$
 dbus-daemon --system --fork$
 /usr/sbin/sshd -D$
 rsyslogd$
 /usr/sbin/mysqld$
 /usr/sbin/apache2 -k start$
EOF
```

```
# List all "suspicious" process
python ./detect_suspicious_process.py --whitelist_file /tmp/whitelist.txt

# List "suspicious" process count
python ./detect_suspicious_process.py --whitelist_file /tmp/whitelist.txt | wc -l
```

# Online Usage
```
Denny:dennyzhang.com denny$ ./detect_suspicious_process.py --help
usage: detect_suspicious_process.py [-h] [--whitelist_file WHITELIST_FILE]

optional arguments:
  -h, --help            show this help message and exit
  --whitelist_file WHITELIST_FILE
                        config file for whitelist
```

# License
- Code is licensed under [MIT License](https://www.dennyzhang.com/wp-content/mit_license.txt).

<img align="right" width="200" height="183" src="https://raw.githubusercontent.com/USDevOps/mywechat-slack-group/master/images/magic.gif">
