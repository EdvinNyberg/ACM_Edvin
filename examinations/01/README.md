# Examination 1 - Understanding SSH and public key authentication

Connect to one of the virtual lab machines through SSH, i.e.

    $ ssh -i deploy_key -l deploy webserver

Study the `.ssh` folder in the home directory of the `deploy` user:

    $ ls -ld ~/.ssh

Look at the contents of the `~/.ssh` directory:

    $ ls -la ~/.ssh/

## QUESTION A

What are the permissions of the `~/.ssh` directory?
drwx for owner only. 

Why are the permissions set in such a way?

Because ssh keys can control other servers by giving them access. So let's say an employee can access the ssh keys, he could put his own pub key in the authorized and enters it from abroad

## QUESTION B

What does the file `~/.ssh/authorized_keys` contain?

The keys to authorize someone entry without needing credentials. It contains a guest list in form of .pub key. If it's approved, then you dont need a password. 

## QUESTION C

When logged into one of the VMs, how can you connect to the
other VM without a password?

You need to put in your pub key into their authorized key. 

### Hints:

* man ssh-keygen(1)
* ssh-copy-id(1) or use a text editor

## BONUS QUESTION

Can you run a command on a remote host via SSH? How?
