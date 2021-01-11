# Copy Files from one computer to another via SSH

The OpenSSH Secure File Copy command is `scp`.

Typical usage and syntax would be in the form of: `scp <source> <destination>`

Recursive (get child folders and files): `scp -r <source> <destination>`

The remote destination needs the account and hostname or IP leading the path. ex: `user@host:/path/to/file`

### To copy a file from B to A while logged into B:
`scp /path/to/file username@a:/path/to/destination`

### To copy a file from B to A while logged into A:
`scp username@b:/path/to/file /path/to/destination`

In summary, you can copy files regardless of current location (ie. local client or in remote session).

# Sync a directory

`rsync` Allows you to copy files similar to how `scp` works but can also delete files in the destination directory if the source does not have them. As the name implies this tool can sync directories (add/remove) with the `--delete` option.

For example if you wanted to sync files to a remote (`-e` for ssh option) server recursively (`-r` option) you could run something like the following: `rsync -e "ssh -i .ssh/SSH_KEY" -r --delete ~/Desktop/test user@IP:/home/Desktop`