# Настройка репозитория.

## Установка git.
_RHEL_
```sh
sudo dnf install git-all
```
_DEB_
```sh
sudo apt install git
```
## Настройка git.
```sh
git config --global user.name "Your Name"
git config --global user.email you@example.com
git config --global alias.history "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
```
## Клонирование репозитория.
```sh
mkdir /path/to/mydir
cd /path/to/mydir
git clone git@github.com:AlexeyBabkinD/sf_team.git
cd sf_team
```
Папку `/path/to/mydir/sf_team` можно добавить в свой IDE и далее работать с кодом через IDE.

# Внесения своих изменений в основную кодовую базу.
Основные ветки - `master` и `develop`.
Добавить изменения возможно только при создании `Pull Request`

## Обновляем develop до последней версии.
```sh
cd /path/to/mydir/sf_team
git checkout develop
git pull
```
## Создаем новую ветку.
Правила именования веток:
- Ветки функциональностей (Feature branches)
Ветки функциональностей могут иметь произвольные названия, которые очень кратко описывают суть задачи, для которой они создаются. Порождается от ветки develop и используются для внедрения в проект дополнительных функций (фич), после чего вливается обратно в develop.

- Ветки релизов (Release branches)
Название имеет вид release-*. Когда появляется надобность в новом релизе, создаётся ветка релиза, происходящая от develop, в которой происходят косметические изменения, необходимые для релиза. После этого ей присваивается версия (тег) в соответствии с принятым в компании стандарте нумераций версий и она вливается в обе основные ветки, master и develop.

- Ветки исправлений (Hotfix branches)
Название имеет вид hotfix-*. Если в текущей стабильной версии проекта (которая хранится в master) выявляется баг, который требует немедленного исправления, создаётся ветка багфикса (исправления), порождённая от master. После удачного исправления бага вливается в master и develop.

```sh
git checkout -b "New-branch-name" develop
```
Далее вносим изменения в новую ветку.

## Сохранение изменений.
- Проверяем какие файлы изменились/добавились/удалились:
```sh
git status
```
- Добавляем файлы которые хотим сохранить:
```sh
git add file1 file2 ... fileN
```
- Сохраняем (коммитим) изменения:
```sh
git commit -m "Commit message"
```
- Отправляем изменения в Github:
Если это первая отправка:
```sh
git push --set-upstream origin "New-branch-name"
```
Если это не первая отправка:
```sh
git push
```
## Добавление изменений в основную ветку.
Создаем Pull Request через веб интерфейс Github или через командную строку.
```sh
git request-pull "New-branch-name" https://github.com/AlexeyBabkinD/sf_team develop
```
После прохождения ревью и получения апрувов мержим ветку.
