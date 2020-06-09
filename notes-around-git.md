# Get around SSH problem
- When confronted with an error

>ssh: connect to host github.com port 22: Operation timed out fatal: Could not read from remote repository

- This reason below justified my error

> Sometimes, firewalls refuse to allow SSH connections entirely. If using HTTPS cloning with credential caching is not an option, you can attempt to clone using an SSH connection made over the HTTPS port. Most firewall rules should allow this, but proxy servers may interfere

- To verify if the above is correct type in `ssh -T git@github.com` and this should time out

## Solution
    - a. sudo nano ~/.ssh/config
    - b. paste this modification here
      > Host github.com
        Hostname ssh.github.com
        Port 443

### Check if the solution suggested above fixed it
    - type `ssh -T git@github.com`