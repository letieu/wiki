# Install window 10 guest

## Install (Host)

```bash
sudo pacman -S qemu-full virt-manager libvirt dnsmasq

# Active service
sudo systemctl start libvirtd

# Add user to libvirt group
sudo usermod -a -G libvirt $USER
```

## Create VM for Window guest (Host)
- CPU: set `Topology` to (socket: 1, cores: 4, threads: 2)
- Disk:
    - CD1: `window.iso` file
    - Virtual disk: set `Disk bus` to `VirtIO`
    - CD2: `virtio-win.iso` file
- Enable boot menu, keep correct disk boot order: CD1 -> Virtual Disk -> CD2
- NIC: set `Device model` to `virtio`

## Install window (Guest)
- Select Install with custom driver
- Choose version of virtio for window
    - select: `E:\viostor\w10\amd64\`
- Next -> next -> ...

## Config window (Guest)
- Device manager:
    - Other device -> Ethernet controller -> Install driver from `CD2`
    - Display adapters -> Install driver from `CD2`

- Install `spice guest tool` (Download from internet)
- Restart

## Change `vgamem` size for the bester display (Host)
- Enable edit `XML` file on `virt manager` -> `preferences`
- VM info -> `Video QXL` -> edit `XML`
- Change `vgame` to `262144` (512 * 512)

## Try use quickemu, may be it can do bester
- [quickemu](https://github.com/quickemu-project/quickemu/wiki/04-Create-Windows-virtual-machines)
