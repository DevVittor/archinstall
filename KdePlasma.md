![ArchLinux](https://i.imgur.com/0ymyIsS.png)

# KDE Plasma

Faça o login colocando o nome do usuário que você cadastrou e a senha.

## Atualizando por completo o arch linux

```bash
sudo pacman -Ssy
```

## Fazendo a instalação do ambiente gráfico

```bash
sudo pacman -S plasma dolphin ark gwenview kitty firefox vlc
```

## Instalação de servidor de áudio e codex

```bash
sudo pacman -S pipewire pipewire-alsa pipewire-jack pipewire-pulse gstreamer gst-libav gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly ffmpeg
```

## Fonts

```bash
sudo pacman -S ttf-roboto ttf-opensans ttf-jetbrains-mono-nerd
```

## Habilitar os serviços do sddm

```bash
sudo sistemctl enable sddm
```

## Habilitar o pipewire

```bash
systemctl --user enable pipewire pipewire-pulse
```

## Reiniciar o Pc

```bash
shutdown -r now
```
