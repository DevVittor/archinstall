# Hyperland

Agora eu vou fazer a instalação do window Manage Hyperland

## Instalando pacotes

```bash
sudo pacman -Syu
```

```bash
sudo pacman -S pipewire pipewire-alsa pipewire-jack pipewire-pulse wireplumber gstreamer gst-libav gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly ffmpeg
```

```bash
sudo pacman -S git
```

```bash
git clone https://aur.archlinux.org/yay
```

```bash
ls
```

```bash
cd yay
```

```bash
ls
```

```bash
makepkg -si
```

```bash
cd
```

```bash
rm -rf yay
```

## Esses são os pacotes que são obrigatórios instalar

| Pacote                      | Obrigatório | Descrição |
| --------------------------- | ----------- | --------- |
| hyprland                    | Sim         |           |
| xdg-desktop-portal-hyprland | Sim         |           |
| xdg-desktop-portal-gtk      | Sim         |           |
| qt5-wayland                 | Sim         |           |
| qt6-wayland                 | Sim         |           |
| hyprlock                    | Não         |           |
| hyprcursor                  | Não         |           |
| hyprpaper                   | Não         |           |
| hyprpicker                  | Não         |           |
| waybar                      | Não         |           |
| kitty                       | Não         |           |
| rofi-wayland                | Não         |           |
| dolphin                     | Não         |           |
| dolphin-plugins             | Não         |           |
| ark                         | Não         |           |
| kio-admin                   | Não         |           |
| dunst                       | Não         |           |
| cliphist                    | Não         |           |
| mpv                         | Não         |           |
| pavucontrol                 | Não         |           |
| xdg-user-dirs-gtk           | Não         |           |
| ttf-font-awesome            | Não         |           |
| ttf-jetbrains-mono-nerd     | Não         |           |
| ttf-opensans                | Não         |           |
| noto-fonts                  | Não         |           |
| ttf-droid                   | Não         |           |
| ttf-roboto                  | Não         |           |

### Obrigatórios

```bash
sudo pacman -S hyprland xdg-desktop-portal-hyprland xdg-desktop-portal-gtk qt5-wayland qt6-wayland polkit-kde-agent
```

### Opcionais

> E esses são os que podem instalar quando estiver dentro do hyperland:

```bash
sudo pacman -S hyprlock hypridle hyprcursor hyprpaper hyprpicker waybar kitty rofi-wayland dolphin dolphin-plugins ark kio-admin dunst cliphist mpv pavucontrol xdg-user-dirs-gtk ttf-font-awesome ttf-jetbrains-mono-nerd ttf-opensans noto-fonts ttf-droid ttf-roboto
```

### Todos os pacotes

```bash
sudo pacman -S hyprland hyprlock hypridle hyprcursor hyprpaper hyprpicker waybar kitty rofi-wayland dolphin dolphin-plugins ark kio-admin polkit-kde-agent qt5-wayland qt6-wayland xdg-desktop-portal-hyprland xdg-desktop-portal-gtk dunst cliphist mpv pavucontrol xdg-user-dirs-gtk ttf-font-awesome ttf-jetbrains-mono-nerd ttf-opensans noto-fonts ttf-droid ttf-roboto
```

```bash
yay -S --noconfirm hyprshot wlogout qview
```

```bash
systemctl --user enable pipewire pipewire-pulse wireplumber
```

## Reinicie o pc

```bash
shutdown -r now
```

## Pra iniciar digite o comando

```bash
hyprland
```
