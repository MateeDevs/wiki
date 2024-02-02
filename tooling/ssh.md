# Matee Wiki - Tooling - SSH

## Matee servers
- [CI/CD](https://github.com/MateeDevs/wiki-private/blob/main/cicd.md)

## Setup on macOS based client

### Copy your public key to the server
- `[your_public_key]` is usually named `id_rsa.pub` or `id_ed25519.pub`
- If password authentication is disabled, this must be done by someone who already has a public key on the server
```
ssh-copy-id -i ~/.ssh/[your_public_key] [user]@[host_name] -p [port]
```

### Connect to the server
```
ssh [user]@[host_name] -p [port]
```

### Create a new host to connect easily
- Add the server to your `~/.ssh/config` in order to connect just by `ssh [alias]`:
```
Host [alias]
  User [user]
  HostName [host_name]
  Port [port]
  IdentityFile ~/.ssh/[your_public_key]
```

### Connect to VNC server
- Create SSH tunnel to the server: `ssh -L 5900:localhost:5900 [alias]`
- Open VNC client: `vnc://localhost` in Safari
- You can create an alias in your `~/.zshrc` in order to connect just by `vnc`:
```
alias vnc='/usr/bin/open -a Safari vnc://localhost && ssh -L 5900:localhost:5900 [alias]'
```

## Setup on macOS based server

### Start/stop SSH 
```
sudo systemsetup -setremotelogin on
sudo systemsetup -setremotelogin off
```

### Disable password authentication
- To prevent authentication without publickey, in the `/etc/ssh/sshd_config` file, set:
```
PasswordAuthentication no
KbdInteractiveAuthentication no
UsePAM no
```

### Restart SSH daemon
- Required to register changes in the config file
```
sudo launchctl stop com.openssh.sshd
sudo launchctl start com.openssh.sshd
```

### Start VNC server
- System Preferences -> Sharing -> Screen Sharing