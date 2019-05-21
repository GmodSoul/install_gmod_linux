1) Загружаем 32-ух битные библеотеки
***
```bash
	sudo apt-get install lib32gcc1
```

2) Создаем отдельного пользователя для сервера
***
```bash
	adduser gmodsoul
```
***
	2.1) Придумываем ему пароль (например gmodsoul228)
***

3) Заходим из под созданного пользователя
***
```bash
	su gmodsoul
```
***

4) Теперь создади несколько папок которые нам пригодяться в будубщем
***

### Переходим в домашнию деректорию и далее в нашего ново испеченого пользователя 
***
```bash
	cd /home/gmodsoul
```

	
### Далее создаем коталоги которые нам потребуются 
***
```bash
	mkdir content server steamcmd content/css
```
***

5) Теперь переходим к основному скачиваем дистрибутив и распаковываем его
***
### Переходим в созданую нами ранее дерикторию steamcmd 
***
```bash	
	cd steamcmd
```
***
### Скачиваем дистрибутив с серверов Valve 
***
```bash
	wget http://media.steampowered.com/client/steamcmd_linux.tar.gz
```
***
### Распаковываем архив в текущую папку 
***
```bash
	tar -xvzf steamcmd_linux.tar.gz
```
***
6) Все готово теперь обновим steamcmd
***
### Cоздаем файл update_steamcmd.sh 
***
```bash
	nano update_steam.sh
```
***
### Записываем в файл последовательность команд 
***
```bash
	./steamcmd.sh +login anonymous +quit
```
***
### Теперь выдвдим файлу права на исполнение 
***
```bash
	chmod +x update_steamcmd.sh
```
***
### Можно запускать файл 
***
```bash
	./update_steamcmd.sh
```
***
7) Далее создадим файл  update_gmod_server.sh (Делаем все тоже самое что и в пункте 6)
***
### Только в файл записываем немного другие команды 
***
```bash
	./steamcmd.sh +login anonymous +force_install_dir "/home/gmodsoul/server" +app_update 4020 validate +quit
```
***
### Теперь выдадим файлу права на исполнение 
***
```bash
	chmod +x update_gmod_server.sh
```
***
### Можно запускать файл 
***
```bash
	./update_gmod_server.sh
```
***
8) После того как мы закачали сервер, можно произвести первый запуск
***
### Идем в папку server 
***
```bash
	cd /home/gmodsoul/server
	ls
```
***
9) Для запуска сервера создадим файл в папку server с название start.sh
***
### Cоздаем файл start.sh 
***
```bash
	nano start.sh
```
***
### Записываем в файл последовательность команд 
***
```bash
	./srcds_run -console -game garrysmod -port 27015 +maxplayers 20 +gamemode sandbox +map gm_construct
```
***
### Теперь выдадим файлу права на исполнение 
***
```bash
	sudo chmod +x start.sh
```
***
### Можно запускать файл 
***
```bash
	./start.sh
```
***
***
----------------------------------- Возможнные ошибки при запуске
***
***

***/srcds_linux: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory***
***
### Решение 
***
```bash
 apt-get install lib32stdc++6
```
***
***
 ***WARNING: Failed to load 32-bit libtinfo.so.5 or libncurses.so.5.***
  ***Please install (lib32tinfo5 / ncurses-libs.i686 / equivalent) to enable readline.***
***
***
### Решение 
***
```bash
	sudo apt-get install lib32tinfo5
```
