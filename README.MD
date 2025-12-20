![ArchLinux](https://i.imgur.com/WC7LNJh.jpeg)
<<<<<<< HEAD
=======

>>>>>>> c322888 (Fix: Agora tem a descrição de cada pacote instalado)
# Instalando o Arch Linux Manualmente em 2025

Vai ter coisa melhor para ser fazer do que aprender bash em 2026, e o caminho exelencente para se evoluir no aprendizagem é baixar e instalar que para mim é a melhor em questão de otimização, estilização e compatibilidade.\
Com esses comando você vai ser possível você instalar o arch Linux sem precisar usar o comando `archinstall`.

## Baixar iso do Arch Linux

| Servidores do **Brasil** para baixar a `.iso`:

- [c3sl.ufpr.br](https://archlinux.c3sl.ufpr.br/iso/2025.12.01/)
- [cicku.me](https://br.mirrors.cicku.me/archlinux/iso/2025.12.01/)
- [ufscar.br](https://mirror.ufscar.br/archlinux/iso/2025.12.01/)
- [unicamp.br](https://mirrors.ic.unicamp.br/archlinux/iso/2025.12.01/)

## Comando Simples usados mount

| Comandos  | Função                                                                                   |
| --------- | ---------------------------------------------------------------------------------------- |
| ls        | Lista arquivos e diretórios do diretório atual                                           |
| cd        | Muda o diretório atual                                                                   |
| lsblk     | Lista dispositivos de bloco (discos, SSDs, partições) e seus pontos de montagem          |
| mount     | Monta um sistema de arquivos em um diretório                                             |
| rm -rf    | Remove arquivos e diretórios de forma forçada e recursiva                                |
| mkdir     | Cria diretórios                                                                          |
| cat       | Exibe o conteúdo de arquivos de texto no terminal ou concatena arquivos                  |
| systemctl | Gerencia serviços do systemd (iniciar, parar, habilitar no boot)                         |
| echo      | Imprime texto no terminal ou escreve texto em arquivos quando usado com redirecionamento |
| shutdown  | Desliga ou reinicia o sistema                                                            |
| exit      | Encerra a sessão atual do shell                                                          |

## Aumenta o tamanho da Fonte do terminal

```bash
setfont ter-132b
```

## Deixa o teclado em abnt-2

```bash
loadkeys br-abnt2
```

Resultado:

![loadkeys](https://i.imgur.com/3F9b8g7.jpeg)

## Testando a internet (A cabo)

```bash
ping -c 3 archlinux.org
```

![Ping](https://i.imgur.com/NLjfR3u.jpeg)

> Se estiver usando o wi-fi procure saber mais

## Checar se iniciou o sistema no modo efi

```bash
ls /sys/firmware/efi
```

![caminho do efi](https://i.imgur.com/cCcRCVd.jpeg)

> Se retornar que o diretório não existe, você inicio de maneira errada.

## Fazendo uma listagem de todos os hds/ssds que tem na máquina

```bash
lsblk
```

| Resultado:

![Resultado no meu terminal](https://i.imgur.com/q3pmKFp.jpeg)

## Selecionar o dispositivo que você quer instalar o arch linux

```bash
cfdisk /dev/sda
```

> Assim que for pra selecionar o tipo de particionameto você escolhe o `gpt`

![label type](https://i.imgur.com/PwGzN8Z.jpeg)

- A primeira partição vai ser no valor de `256m`
- A segunra partição vai ser no valor de `10g`
- A terceira partição vai ficar no valor de `15g`
- E a quarta partição vai ficar com a quantidade de giga que sobrou

![sda](https://i.imgur.com/UEs6R34.jpeg)

> O megabytes é representada por `m` e o gigabyte por `g`.

| Depois só precisa clicar em `Write` e depois digitar `yes` e clicar logo em seguida em `Quit`

## Partições

Vão ser 4 partições a primeira com `256m` com o type `EFI System` 2º Partição vai ter `20g` do tipo `Linux filesystem` e a 3º partição só vai ter de diferente da 2º o tamanho do gigas em vez de ser `20g` vai ser `25g` mas com o mesmo type e a 4º partição vai ficar com o que sobrou e colocar o type de `Linux swap` da um `write` e digite `yes` e depois clique em `quit`

```bash
lsblk
```

Resultado:

![Resultado no meu terminal](https://i.imgur.com/4flAJhi.jpeg)

| Exibe uma visão clara e hierárquica (em formato de árvore) dos seus dispositivos de armazenamento, como:

- Discos rígidos (HDDs/SSDs)
- Partições
- Volumes lógicos (LVM)
- Dispositivos de CD/DVD (ROMs)
- Pendrives ou outras mídias removíveis

## 📂 Formatar partições

```bash
mkfs.fat -F32 /dev/sda1
```

Resultado:

![mksfs.fat sda1](https://i.imgur.com/nWZlpYH.jpeg)

```bash
mkfs.ext4 /dev/sda2
```

Resultado:

![mkfs.ext4 sda2](https://i.imgur.com/Ixlg3x8.jpeg)

```bash
mkfs.ext4 /dev/sda3
```

Resultado:

![mkfs.ext4 sda3](https://i.imgur.com/oI4lxHI.jpeg)

```bash
mkswap /dev/sda4
```

Resultado:

![mkswap sda4](https://i.imgur.com/qlgH9kg.jpeg)

## 📌 Montar partições

```bash
mount /dev/sda2 /mnt
```

```bash
mkdir /mnt/home
```

```bash
mkdir /mnt/boot
```

```bash
mkdir /mnt/boot/efi
```

```bash
ls /mnt
```

Resultado:

![ls mnt](https://i.imgur.com/5OWliSf.jpeg)

```bash
mount /dev/sda3 /mnt/home
```

```bash
mount /dev/sda1 /mnt/boot/efi
```

```bash
swapon /dev/sda4
```

## 🚀 Instalação do sistema base

```bash
lsblk
```

Resultado:

![lsblk mount](https://i.imgur.com/gdwJlYd.jpeg)

```bash
pacman -Sy
```

```bash
pacman -S reflector
```

```bash
reflector --country Brazil --latest 20 --sort rate --verbose --save /etc/pacman.d/mirrorlist
```

Resultado:

![reflector](https://i.imgur.com/qbF3VcS.jpeg)

```bash
nano /etc/pacman.d/mirrorlist
```

Resultado:

![pacman List](https://i.imgur.com/SOkHGbF.jpeg)

```bash
pacstrap /mnt base base-devel linux linux-headers linux-firmware nano vim
```

## 🧾 Gerar fstab

```bash
genfstab /mnt
```

Resultado:

![genfstab mnt](https://i.imgur.com/ySQlPvD.jpeg)

```bash
genfstab -U /mnt >> /mnt/etc/fstab
```

```bash
cat /mnt/etc/fstab
```

Resultado:

![cat fstab](https://i.imgur.com/xmOceux.jpeg)

| Confirir se jogou essas informações corretamente

```bash
ls /mnt
```

Resultado:

![ls mnt](https://i.imgur.com/O6aepLJ.jpeg)

## 🔐 Entrar no sistema instalado

```bash
arch-chroot /mnt
```

Resultado:

![arch chroot](https://i.imgur.com/ZIAafi0.jpeg)

```bash
nano /etc/pacman.conf
```

![pacman conf](https://i.imgur.com/tIcIQzJ.jpeg)

| Remover os comentários de Color e aumentar o valor de ParellelDownloads de 5 para 10
| E dentro do arquivo ainda vai em [multilib] e remova o comentário do Include e salve e sai do arquivo.

Resultado:

![multilib](https://i.imgur.com/ir81VeT.jpeg)

## 🕒 Fuso horário

```bash
ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime
```

```bash
hwclock --systohc
```

```bash
timedatectl set-ntp true
```

```bash
date
```

Resultado:

![date](https://i.imgur.com/qzHwXH5.jpeg)

## 🌍 Idioma

```bash
nano /etc/locale.gen
```

Resultado:

![nano locale gen ](https://i.imgur.com/BPzPFcP.jpeg)

> Selecione o idioma que você quer no seu sistema eu escolhi o `pt_BR.UTF-8 UTF-8`

```bash
locale-gen
```

Resultado:

![locale gen](https://i.imgur.com/qbY8EW8.jpeg)

```bash
echo "LANG=pt_BR.UTF-8" >> /etc/locale.conf
```

Verificar:

```bash
nano /etc/locale.conf
```

Resultado:

![nano locale gen ](https://i.imgur.com/xBbBCss.jpeg)

## ⌨️ Teclado

```bash
echo "KEYMAP=br-abnt2" >> /etc/vconsole.conf
```

Verificar:

```bash
nano /etc/vconsole.conf
```

Resultado:

![vconsole](https://i.imgur.com/imrw9yr.jpeg)

## 🖥️ Hostname

```bash
echo "archlinux" >> /etc/hostname
```

Verificar:

```bash
nano /etc/hostname
```

Resultado:

![hostname](https://i.imgur.com/jln1Wt7.jpeg)

```bash
nano /etc/hosts
```

Resultado:

![hosts](https://i.imgur.com/nDtyUGV.jpeg)

## 🔑 Usuários e permissões

```bash
passwd
```

Resultado:

![passwd](https://i.imgur.com/rA5Rtls.jpeg)

## Muito cuidado na hora de editar esse arquivo pq ele pode acabar com o sistema inteiro

```bash
nano /etc/sudoers
```

Resultado:

![sudoers](https://i.imgur.com/1WOONkR.jpeg)

> Remova os comentários apenas do comando `%whell ALL=(ALL:ALL) ALL`

## Escolhendo o nome de usuário

```bash
useradd -mG wheel (Escolha um nome de usuário)
```

## Criando a senha do usuário

```bash
passwd (Nome do usuário)
```

Resultado:

![passwd user](https://i.imgur.com/DHPYMQ6.jpeg)

## 🧰 Bootloader e rede

| Pacote         | Descrição                                                                                                                     |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| dosfstools     | Utilitários para criar e verificar sistemas de arquivos FAT (FAT16/FAT32), usados principalmente em partições EFI e pendrives |
| mtools         | Conjunto de ferramentas para acessar e manipular sistemas de arquivos FAT sem precisar montá-los                              |
| os-prober      | Detecta outros sistemas operacionais instalados no disco para que sejam adicionados automaticamente ao GRUB                   |
| networkmanager | Serviço responsável por gerenciar conexões de rede (Wi-Fi, Ethernet, VPN), usado pela maioria dos ambientes gráficos          |
| grub           | GRand Unified Bootloader, responsável por carregar o sistema operacional durante a inicialização                              |
| efibootmgr     | Ferramenta para criar, remover e gerenciar entradas de boot UEFI diretamente no firmware                                      |

```bash
pacman -S dosfstools mtools os-prober networkmanager grub efibootmgr
```

> Preste muito atenção se está tudo sendo digitado corretamente porque se houver qualquer tipo de error você tera que instalar tudo novamente.

```bash
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=archlinux --recheck
```

Resultado:

![grub install](https://i.imgur.com/0cHNMYr.jpeg)

## Se for fazer dualboot com windows

```bash
nano /etc/default/grub
```

Resultado:

![grub disable](https://i.imgur.com/brcTzoq.jpeg)

> Remova os comentários do comando `GRUB_DISABLE_OS_PROBER=false`

```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

Resultado:

![grub mkconfig](https://i.imgur.com/UHs9Hz1.jpeg)

```bash
systemctl enable NetworkManager
```

Resultado:

![systemctl NetworkManager](https://i.imgur.com/veGkxOV.jpeg)

## 🔄 Finalização

```bash
exit
```

Resultado:

![exit terminal](https://i.imgur.com/9a9ElW3.jpeg)

```bash
shutdown -r now
```

🎉 Arch Linux instalado com sucesso!
Agora você tem um sistema limpo, rápido e totalmente sob seu controle.
Mas você precisa seguir outra documentação pra ter um gerenciador de janelas, `kde plasma`, `gnome` ou `hyprland`
