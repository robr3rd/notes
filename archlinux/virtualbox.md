# Arch Linux - VirtualBox

## Loading Guest Services
Usually I see a notification message like `VBoxClient service failed to 
load` pop up every time I boot and it won't go away. This is what it's 
complaining about.

- [Arch Wiki](https://wiki.archlinux.org/index.php/VirtualBox#Launch_the_VirtualBox_guest_services)

Basically, the problem is that `VBoxClient-all` needs to be run so 
that VirtualBox's convenience features such as "Shared 
Clipboard", "Drag-and-Drop", and so on will work.

This script ties into the `vboxservice` backend service, which is 
generally not enabled out-of-the-box.

### Step-by-Step
- `sudo systemctl start vboxservice`
- `sudo systemctl enable vboxservice`
- `sudo VBoxClient-all` (now you're good to go for this boot, but this 
still needs to happen every time)

Now we'll want to automate this process with an autostart script...(for 
GNOME):

```
# ~/.config/autostart/vboxclient-all.desktop

[Desktop Entry]
Name=VBoxClient-all
GenericName=Autostart all VBoxClient services on boot
Comment=Autostart all VBoxClient services on boot
Exec=/usr/sbin/VBoxClient-all
Terminal=false
Type=Application
X-GNOME-Autostart-enabled=true
```

For reference, the `.desktop` file specs:
- [Desktop Entry](https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)
- [Autostart](https://specifications.freedesktop.org/autostart-spec/autostart-spec-latest.html)
