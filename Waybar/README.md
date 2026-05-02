# dotfiles

Meine persönlichen Dotfiles für Hyprland auf omarchy.

## Abhängigkeiten

### swaync (Notification Daemon)

Diese Dotfiles verwenden **swaync** als Notification Daemon. Da omarchy standardmäßig mako mitbringt, muss swaync manuell installiert werden:

```bash
yay -S swaync
# oder
paru -S swaync
```

### mako deaktivieren

omarchy startet mako automatisch über einen systemd User Service. Dieser muss deaktiviert werden, sonst funktioniert swaync nicht korrekt:

```bash
systemctl --user disable mako
systemctl --user stop mako
```

### swaync in den Autostart

swaync in die Hyprland Autostart-Config eintragen (`~/.config/hypr/autostart.conf`):

```
exec-once = swaync
```

Dann den systemd Service aktivieren damit er beim Login startet:

```bash
systemctl --user enable --now swaync
```
