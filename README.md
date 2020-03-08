## Попасть в систему без пароля несколькими способами
### Способ 1. init=/bin/sh
1. В конце строки, начинающейся с linux16, добавляем init=/bin/sh и нажимаем ctrl-x для загрузки в систему
2. Перемонтируем рутовую ФС в режим Read-Write
```
mount -o remount,rw /
```
### Способ 2. rd.break
1. В конце строки, начинающейся с linux16, добавляем rd.break и нажимаем ctrl-x для загрузки в систему
2. Попадаем в emergency mode. ФС смонтирована, но мы не в ней. Необходимо попасть в нее и поменять пароль администратора
```
mount -o remount,rw /sysroot
chroot /sysroot
passwd root
touch /.autorelabel
exit
reboot
```
### Способ 3. rw init=/sysroot/bin/sh

1. В конце строки, начинающейся с linux16, ro на rw init=/sysroot/bin/sh и нажимаем ctrl-x для загрузки в систему

```
chroot /sysroot
passwd root
touch /.autorelabel
exit
reboot
```
## Установить систему с LVM, после чего переименовать VG
Проделанные [действия](typescript_vgs), записанные с помощью утилиты script

## Добавить модуль в initrd
Проделанные [действия](typescript_module), записанные с помощью утилиты script

Пингвин в выводе терминала:
![screen](https://sun9-7.userapi.com/c857136/v857136368/1101df/Rqu6qw-VFek.jpg)
