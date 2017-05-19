# LINKS

---

[I'm an inline-style link with title](https://www.google.com "Google's Homepage")

```[I'm an inline-style link with title](https://www.google.com "Google's Homepage")```

---

**Easy way to create custom code**
https://generatewp.com

---

**Custom Fields**

https://cmb2.io

http://pods.io

http://www.advancedcustomfields.com

---

**How to use SFTP to connect to Amazon EC2**

Yes, it is possible to enable ssh / sftp root access.

To do so, connect as ec2-user with ssh

    sudo bash (to gain root privileges)
    edit /etc/ssh/sshd_config and change these two lines from


#PermitRootLogin yes
PermitRootLogin forced-commands-only

to

PermitRootLogin yes
#PermitRootLogin forced-commands-only

    restart ssh daemon


root@ip-10-235-67-181 ec2-user# service sshd stop
Stopping sshd: OK
root@ip-10-235-67-181 ec2-user# service sshd start
Starting sshd: OK

    edit /root/.ssh/authorized_keys


and remove everything from the start of the line to ssh-rsa ...
Your new line MUST start with ssh-rsa

    then exit the root session, exit the ec2-user session and try to connect with root user


The key to use is the same as the key used for ec2-user (Amazon Linux is configured with the same key for ec2-user and root user)

For security reason, it is advised to undo your changes when you're finish to edit your configuration files. (switch back to original sshd_config and restart ssh service again)

**Found here** - *https://forums.aws.amazon.com/thread.jspa?threadID=120241*

---

