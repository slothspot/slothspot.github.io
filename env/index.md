---
title: Work Environment
layout: page
---
Ниже будут приведены заметки по настройке рабочего окружения на базе Linux-дистрибутива [Fedora](http://fedoraproject.org).

### BFO

У проекта Fedora есть сервис для упрощения сетевой установки разных версий дистрибутива -
[BFO](https://boot.fedoraproject.org/). Именно им мы и воспользуемся чтобы получить образ,
для создания загрузочной флешки. В секции [Download](https://boot.fedoraproject.org/download)
находим вариант [образа для USB](http://dl.fedoraproject.org/pub/alt/bfo/bfo.usb).

С помощью команды *cat* зальем скачанный образ на флеш-накопитель. (В примере ниже накопителю
отвечает устройство */dev/sdc*):
{% highlight bash %}
cat bfo.usb > /dev/sdc
{% endhighlight %}

### Загрузка компьютера/ноутбука и установка системы

Тут следует стандартная установка дистрибутива и на ней останавливаться не буду

### Настройка

#### Broadcom Wireless Drivers (BCM43225)

Для утановки драйверов нужно подключить *nonfree* репозиторий [rpmfusion](http://rpmfusion.org/Configuration).
После подключения репозитория, выполнить следующую команду:
{% highlight bash %}
$ sudo yum install kmod-wl
{% endhighlight %}

#### Командная оболочка

В качестве оболочки используется [Zsh](http://www.zsh.org/). Для ее установки выполнить следующие команды:
{% highlight bash %}
$ sudo yum install zsh
$ sudo chsh -s /bin/zsh
{% endhighlight %}

#### Текстовый редактор

В качестве редактора используется [Vim](http://www.vim.org/). Для его установки выполнить следуюшую команду:
{% highlight bash %}
$ sudo yum install vim-enhanced ruby
{% endhighlight %}

#### Оконный менеджер

В качестве оконного менеджера используетс [i3wm](http://i3wm.org/). Для установки выполнить
следующую команду(также устанавливает простой локер экрана и генератор строки статуса):

{% highlight bash %}
$ sudo yum install i3 i3lock i3status
{% endhighlight %}

#### dotfiles

Настройки наиболее важных приложений для моего рабочего окружения расположены на [github](https://github.com).
Ниже немного [git](http://git-scm.com/)-магии для получения копии репозитория в домашней директории пользователя:

{% highlight bash %}
$ git init
$ git remote add origin https://github.com/slothspot/configs.git
$ git fetch
$ git checkout -t origin/master
{% endhighlight %}

#### Other

TODO
