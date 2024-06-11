# Matee Wiki - Tooling - SSH

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
  IdentityFile ~/.ssh/[your_private_key]
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
