# Users & Groups
##Contents:
1. Где Linux хранит информацию о пользователях
2. UID и GID
3. Information about users
4. Groups informations
5. Users & groups

# 1. Где Linux хранит информацию о пользователях
<details>
Основные файлы:

```
/etc/passwd   → информация о пользователях
/etc/shadow   → пароли и параметры паролей
/etc/group    → группы
/etc/gshadow  → защищённая информация о группах
```

cat /etc/passwd - посмотреть  

пример:  
trinity:x:1000:1000:Trinity:/home/trinity:/bin/bash  

Формат:  
username : password : UID : GID : comment : home : shell  

</details>

# 2. UID и GID
<details>
UID — идентификатор пользователя.  

uid=1000(trinity) gid=1000(trinity) groups=1000(trinity),27(sudo)  

here:  
UID = 1000  
GID = 1000  

Linux фактически работает с числовыми ID, а имена trinity, sudo — это удобное представление для человека.
</details>

# 3. information about users

<details>

```
whoami			- текущий пользователь  
who				- Кто сейчас вошёл в систему  
w				- Показывает, кто вошёл и что сейчас делает.

id				- пакажет больше о пользователе  
getent passwd   - показать все записи пользователей, доступные системе через NSS (Name Service Switch) 
users			- Просто показывает имена пользователей с активными сессиями

cut -d: -f1 /etc/passwd			-посмотреть всех пользователей
cut -d: -f1 /etc/passwd | sort  - посмотреть всех пользователей

awk -F: '$3 >= 1000 {print $1}' /etc/passwd		    - Linux UID обычных пользователей начинаются с 1000: 
awk -F: '$3 >= 1000 {print $1, $3, $6}' /etc/passwd - Можно посмотреть вместе с UID и домашней папкой: 
```

</details>

# 4. Groups information

groups user - посмотреть группы пользователя  
id user		- посмотреть группы пользователя + числовой индефикатор  

# user and groups

<details>

```
sudo useradd user2				  - создать пользователя
sudo useradd -m nameUser		  - создать пользователя и домашний каталог
sudo passwd user				  - пароль для нового пользователя

sudo su user					  - переключает текущую оболочку на другого пользователя 
Но важный момент: это не совсем «выйти из root». Ты создал новую оболочку (shell) пользователя neo внутри текущей сессии root 
sudo -iu user					  - Часто вместо sudo su user используют, Она переключает пользователя и одновременно запускает его login-shell. 


sudo groupadd developers		  - создать группу  
sudo usermod -aG developers user2 - добавить пользователя в группу  
			 -aG				  - означает добавить, не удаляя существующие дополнительные группы.  

sudo gpasswd -d user2 developers  - удалить пользователя из группы  
sudo userdel user				  - удалить пользователя
sudo userdel -r user			  - удалить вместе с домашней директорией
sudo rm -r /home/username		  - удалить папку пользователя
	    -r						  - удаляет /home/user и другие связанные файлы пользователя.


```

</details>
