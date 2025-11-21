# Examination 1 - Understanding SSH and public key authentication

Connect to one of the virtual lab machines through SSH, i.e.

    $ ssh -i deploy_key -l deploy webserver

Study the `.ssh` folder in the home directory of the `deploy` user:

    $ ls -ld ~/.ssh

Look at the contents of the `~/.ssh` directory:

    $ ls -la ~/.ssh/

## QUESTION A

What are the permissions of the `~/.ssh` directory?

A: (drwx------).

Why are the permissions set in such a way?

A: SSH requires that the .ssh directory is only accessible by the owner,
if others can read/write SSH will refuse to use the keys to prevent unauthorized access.

## QUESTION B

What does the file `~/.ssh/authorized_keys` contain?

A: It contains the public key generated on the host and copied to the VM.

## QUESTION C

When logged into one of the VMs, how can you connect to the
other VM without a password?

A: Since both VMs have the same deploy user and the same public key setup you can copy the public key to the other VM if its not already there.

### Hints:

* man ssh-keygen(1)
* ssh-copy-id(1) or use a text editor

## BONUS QUESTION

Can you run a command on a remote host via SSH? How?

A: Yes, you can execute a command directly using

    $ ssh -i ~/.ssh/deploy_key deploy@dbserver "command"
