
## Сохранение паролей для работы с bash или terminal на github.com, bitbucket.org.  


##### 1) Генерация ключей, при генерации будет предложено ввести ключевую фразу (keyphrase)  
*Ключи попадут в ваш домашний каталог в папку .ssh*  
```bash
ssh-keygen -f ~/.ssh/github -C "usermail@gmail.com"
```
```bash
ssh-keygen -f ~/.ssh/bitbucket -C "usermail@gmail.com"
```

##### 2) Стартуем SSH агент:
```bash
eval "$(ssh-agent -s)"
```

##### 3) Добавленяем ключи
```bash
ssh-add ~/.ssh/github
```
```bash
ssh-add ~/.ssh/bitbucket
```

##### 4) Проверим список загруженных ключей
```bash
ssh-add -l
```

##### 5) Удалим ключи (если нужно) 
```bash
ssh-add -D
```

##### 6) Копируем ключ в буфер обмена:  
(Для Mac OS, для Windows по-другому) 
```bash
pbcopy < ~/.ssh/github.pub 
```
```bash
pbcopy < ~/.ssh/bitbucket.pub
```

##### 7) Вставляем каждый ключ в свои аккаунты (Настройки SSH)  

GitHub: https://github.com/settings/keys  
Bitbucket: https://bitbucket.org/account/user/username/ssh-keys/  
*username* - ваше имя пользователя.    
Можно зайти на эти адреса в настройках аккаунтов. 

---

##### Дополнительно: 

В доках для bitbucket пишут, что для нескольких аккаунтов нужно юзать конфиг файл:  
~/.ssh/config   
на маке проверял - этот файл не нужен, и без него работает. 

На всякий случай привожу пример файла: 

```
# GitHub User 
Host github.com
 Hostname ssh.github.com
 Port 443
 User username
 PreferredAuthentications publickey
 IdentityFile ~/.ssh/github

# Bitbucket User
Host bitbucket.org
 HostName bitbucket.org
 User username
 PreferredAuthentications publickey
 IdentityFile ~/.ssh/bitbucket
```

---
##### Ссылки на документацию:  
- https://help.github.com/articles/connecting-to-github-with-ssh/  

- https://confluence.atlassian.com/bitbucket/configure-multiple-ssh-identities-for-gitbash-mac-osx-linux-271943168.html  

- https://wiki.archlinux.org/index.php/SSH_keys_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)  





