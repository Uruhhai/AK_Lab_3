# Platform Bring Up: BeagleBone Black (Linux + QEMU)

## Мета роботи
Побудова мінімальної вбудованої Linux-системи для архітектури ARM з використанням upstream-ядра Linux, статичного BusyBox та емуляції в QEMU.

## Структура проєкту
- `kernel/config` — конфігураційний файл ядра Linux (`CONFIG_DEVTMPFS=y`).
- `busybox/config` — конфігураційний файл BusyBox (`CONFIG_STATIC=y`).
- `rootfs/etc/inittab` — конфігурація ініціалізації для послідовного порту `ttyAMA0`.

## Запуск в QEMU
bash
qemu-system-arm -M virt -cpu cortex-a15 -m 512 

-kernel zImage 

-drive file=rootfs.ext4,format=raw,if=none,id=hd0 

-device virtio-blk-device,drive=hd0 

-append "console=ttyAMA0 root=/dev/vda rw" 

-nographic
