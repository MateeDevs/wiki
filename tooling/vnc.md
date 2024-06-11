# Matee Wiki - Tooling - VNC

## Connect to VNC server

### Locally from macOS based client
- Either type `open vnc://[host_name]:[port]` in Terminal or `vnc://[host_name]:[port]` in Safari or other browser
- You can omit `:[port]` if your server is using a default port (5900)
- A default Screen Sharing app will open and you can type-in VNC username and password

### Over SSH tunnel from macOS based client
- Create SSH tunnel to the server: `ssh -L 5900:localhost:5900 [alias]` (see more about SSH [here](/tooling/ssh.md))
- This will forward everything from the local port 5900 to the remote port 5900 via SSH tunnel
- Open VNC client: `open vnc://localhost` in Terminal or `vnc://localhost` in Safari
- You can create an alias in your `~/.zshrc` in order to connect just by `vnc`:
```
alias vnc='/usr/bin/open -a Safari vnc://localhost && ssh -L 5900:localhost:5900 [alias]'
```

## Setup VNC server

### macOS
- System Preferences -> Sharing -> Screen Sharing

### Ubuntu
- Settings -> Sharing -> Remote Desktop
- Enable Legacy VNC Protocol and in three-dot submenu select "require password" (needed for connections from macOS's Screen Sharing app)
- It's not possible to connect when there are no active user sessions (after restart), as a workaround you can enable Automatic Login in Settings -> Users. However, Automatic Login doesn't unlock GNOME Keyring, so VNC will not be able to accept connections, as a workaround you can set empty password for login Keyring in Passwords and Keys. More information: [How to Enable Remote Desktop in Ubuntu 22.04](https://losst.pro/en/how-to-enable-remote-desktop-in-ubuntu-22-04-23-10#toc-3-install-the-allow-locked-remote-desktop-extension)
- Additionally, if there is no monitor plugged-in, you have to add fake display - [more info](https://askubuntu.com/a/463000)
- You may also encounter issues with clients not able to connect via SSH tunnel randomly. In that case verify the connection on the client via `netstat -an | grep 5900`, if you see `FIN_WAIT` or `CLOSE_WAIT` in there, it means that your connection isn't properly established. You can try adding `ServerAliveInterval 60` and `ServerAliveCountMax 30` to the specific host in your `~/.ssh/config`.
