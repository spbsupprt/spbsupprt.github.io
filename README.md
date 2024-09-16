# Administrator-Linux.-Professional
https://otus.ru/learning/312851/



#ДЗ обновсить ядро в базовой системе

apt-cache search linux-generic

apt install linux-image-6.8.0-41-generic


![image](https://github.com/user-attachments/assets/f768041e-76ea-44fa-9c70-b0906cb3fa2a)

--------------------------------------------------------
#доп собрбать ядро
Шаг 1. Загрузите исходный код 

  1. Посетите официальный сайт ядра www.kernel.org и загрузите последнюю версию. Загруженный файл содержит сжатый исходный код.
  https://www.kernel.org/

  2. Откройте терминал и используйте команду wget для загрузки исходного кода ядра Linux:
  $ wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.10.9.tar.xz

Шаг 2: извлеките исходный код
  $ tar xvf linux-6.10.9.tar.xz

Шаг 3: Установите необходимые пакеты
  $ sudo apt-get install git fakeroot build-essential ncurses-dev xz-utils libssl-dev bc flex libelf-dev bison

Шаг 4: Настройте ядро

  1. Перейдите к каталогу linux-6.10.9. с помощью команды cd:
  $ cd linux-6.10.9

  2. Скопируйте существующий файл конфигурации с помощью команды cp:
  $ cp -v /boot/config-$(uname -r) .config

  3. Чтобы внести изменения в файл конфигурации, выполните команду make:
  $ make defconfig

Шаг 5: Соберите ядро

  1. Начните сборку ядра, выполнив следующую команду:
  $ make

  2. Установите необходимые модули с помощью этой команды:
  $ sudo make modules_install

  3. Наконец, установите ядро, набрав:
  $ sudo make install

Шаг 6. Обновите загрузчик (необязательно)

  Загрузчик GRUB - это первая программа, которая запускается при включении системы.
  Команда make install выполняет этот процесс автоматически, но вы также можете сделать это вручную.

  1. Обновите initramfs до установленной версии ядра:
  $ sudo update-initramfs -c -k 6.10.9

  2. Обновите загрузчик GRUB с помощью этой команды:
  $ sudo update-grub

Шаг 7: Перезагрузите и проверьте версию ядра

  $ uname -m
