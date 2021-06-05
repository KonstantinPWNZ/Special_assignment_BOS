# Работа Семиуглова Константина Б18-565
- Создаю в rpmbuild папки BUILD,BUILDROOT,RPMS,SOURCES,SPECS,SRPMS:
   ```
   mkdir ~/rpmbuild/{BUILD,BUILDROOT,RPMS,SOURCES,SPECS,SRPMS}
   ```
- Клонирую репозиторий из гитхаба в папку SOURCES:
   ```
   git clone https://github.com/parazyd/git-restrict
   ```
- Переименовываю в git-restrict-1.0:
   ```
   mv git-restrict git-restrict-1.0
   ```
- Архивируем данные:
   ```
   tar cvfz git-restrict-1.0.tar.gz git-restrict-1.0
   ```
- Перехожу в папку SOURCES/git-restrict-1.0/ и запускаю test.sh:
   ```
   ./test.sh 
   ```
- Перехожу в папку SPECS, c помощью текстового редактора nano создаю файл git-restrict.spec, а затем выполняю сборку пакета:
   ```
   nano git-restrict.spec
   rpmbuild -ba git-restrict.spec
   ```
- Генерирую ключ для подписания пакета, где будет запрошено ввести имя и почту:
   ```
   gpg2 --gen-key
   ```
- Экспортируем открытую часть ключа:
   ```
   gpg2 --export -a 'Konstantin Semiuglov' > ~/rpmbuild/RPM-GPG-KEY-Konstantin-Semiuglov
   ```
- Создаю марос:
   ```
   echo '%_gpg_name Semiuglov Konstantin' > .rpmmacros
   ```
- Перехожу в папку rpmbuild/RPMS/x86_64 и подписываю все пакеты:
   ```
   rpm --addsign *.rpm
   ```
