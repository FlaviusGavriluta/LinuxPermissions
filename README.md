# Linux Permissions

## Story

You were asked to grant temporary access to your Linux server to a new user. The user provides a username, a password hash and an ssh key. The user also kindly asks you to add him to the `sudo` group.
After you have set everything up the user will test his access to the system with his password and ssh private key.

## What are you going to learn?

- Understand file permissions
- How to edit file permissions using the `chmod` command in octal or symbolic mode
- Special permissions
- Managing users and groups
- Which files contain information about users and groups
- Understand the `/etc/shadow` file
- How to change user/group ownership of a file using the `chown` command
- What is an inode and file metadata

## Tasks

1. Add a new user to the system called `john`.
    - A new user called `john` is added to the system. John has a home directory.

2. Use the provided password hash and place it in the correct file and location.
    - The password hash that was generated upon user creation is replaced with the hash provided by the user.

3. Grant the user SSH access to the system
    - .ssh directory with the correct permissions and ownership is created in the home directory of the user `john`.
    - `authorized_keys` file with the correct permissions and ownership is created in the .ssh directory and the public ssh key provided for the user `john` is copied into the file.

4. Add the user to the `sudo` group
    - The user `john` is added to the `sudo` group.

5. The user doesn't need access to your system anymore so you can delete it.
    - The user and his home directory are deleted from the system.

## General requirements

None

## Hints

- Check the commands `useradd` and `adduser` for creating a new user.
- The password hashes are stored in the `/etc/shadow`. Check the background materials to learn about the structure of this file.
- You can directly replace the hash or use a command `usermod -p $HASH john` to automatically place the hash for the user `john` in `/etc/shadow`.
- The `.ssh` directory permissions should be 700 (drwx------) and the authorized_keys file on the server, should be 600 (-rw-------). They should be owned by the user `john`. Use `chmod` and `chown` commands to set the correct permissions and ownership.
- Test if the ssh connection is working using the provided private key and password. You can pass the key file to the ssh command using the `-i` option. Example: `ssh -p 2222 john@localhost -i id_rsa`.
- Once logged in, check if the `sudo` access is available.

## Background materials

- <i class="far fa-exclamation"></i> [File Permissions in Linux/Unix with Example](https://www.guru99.com/file-permissions.html)
- <i class="far fa-exclamation"></i> [How to Add New Users to Ubuntu 20.04 | 18.04](https://websiteforstudents.com/how-to-add-new-users-to-ubuntu-20-04-18-04/)
- <i class="far fa-exclamation"></i> [Users and groups](https://wiki.archlinux.org/index.php/users_and_groups)
- <i class="far fa-exclamation"></i> [SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
- <i class="far fa-exclamation"></i> [Everything You Ever Wanted to Know About inodes on Linux](https://www.howtogeek.com/465350/everything-you-ever-wanted-to-know-about-inodes-on-linux/)
- <i class="far fa-exclamation"></i> [Chown Command in Linux (File Ownership)](https://linuxize.com/post/linux-chown-command/)
- [Linux permissions: SUID, SGID, and sticky bit](https://www.redhat.com/sysadmin/suid-sgid-sticky-bit)
- [Understanding the /etc/shadow File](https://linuxize.com/post/etc-shadow-file/)

