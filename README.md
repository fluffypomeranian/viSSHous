# viSSHous
### "infect remote ssh sessions with your vim profile"
![Visshous Logo](./icon.jpg)
#### The goal of Visshous is to enable you to automatically transport your .vimrc profile settings when doing work on remote servers, without having to manually 'copy/paste' or 'scp/sftp' files.

--- 

#### Requirements:
 
- plugin manager (if you use one) must be installed manually on remote machine 

#### Quickstart:

From local machine: 

```
sh local.sh
```

```
ssh <remote-server> < remote.sh
```

#### How does it work? 

Visshous exploits the default sshd configuration to pass your vimrc without having to configure extra settings. We do this by using the fact that 'sshd' allows by default 'locale config' variables (see `man locale` if you're curious) to be passed on through a remote host. To exploit this, we simply base64 encode our local .vimrc file, and pass that in through the ssh protocol itself as an env variable. Then, we can simply decode our remote vimrc from that env variable. Because this solution passes the configuration in an 'ssh-native' way, its a bit cleaner . 

#### Tested On:
- [X] Google Cloud
- [ ] IBM Cloud
- [ ] AWS EC2
- [ ] Microsoft Azure
