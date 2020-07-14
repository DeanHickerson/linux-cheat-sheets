# Copy Files from one computer to another via SSH

The OpenSSH Secure File Copy command is `scp`.

Typical usage and syntax would be in the form of: `scp <source> <destination>`

### To copy a file from B to A while logged into B:
`scp /path/to/file username@a:/path/to/destination`

### To copy a file from B to A while logged into A:
`scp username@b:/path/to/file /path/to/destination`

In summary, you can copy files regardless of current location (ie. local client or in remote session).

