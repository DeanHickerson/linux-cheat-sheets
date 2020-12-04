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

