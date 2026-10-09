# Git — шпаргалка

## 1. Основные понятия

* **Git** — система контроля версий, отслеживает изменения файлов.
* **Repository (репозиторий)** — проект, история изменений которого хранится в Git.
* **Commit** — сохранённый снимок изменений.
* **Branch** — отдельная ветка разработки.
* **Remote** — удалённый репозиторий, например GitHub или GitLab.
* **Push** — отправка коммитов на удалённый сервер.
* **Pull** — получение изменений с сервера и их интеграция в текущую ветку.
* **Clone** — копирование удалённого репозитория на компьютер.
* **Staging area** — область подготовки файлов перед коммитом.

## 2. Первоначальная настройка
<details>

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --list
```

</details>
## 3. Создание репозитория
<details>

```bash
git init                 # создать локальный репозиторий
git clone URL            # клонировать репозиторий
git status               # проверить состояние файлов
```

</details>
## 4. Основной рабочий цикл
<details>

```bash
git status                       # проверить изменения
git add file.md                  # добавить конкретный файл
git add Linux/                   # добавить папку
git add .                        # добавить все изменения
git diff                         # изменения до git add
git diff --cached                # подготовленные изменения
git commit -m "Update notes"     # создать коммит
git log --oneline                # краткая история коммитов
```

**Важно:** `git add` подготавливает изменения, `git commit` сохраняет их в истории, `git push` отправляет коммиты на сервер.
</details>
## 5. Отправка на GitHub и GitLab
<details>

```bash
git remote -v                    # показать удалённые репозитории
git push origin main             # отправить на GitHub
git push gitlab main              # отправить на GitLab
git pull origin main              # получить и интегрировать изменения
git fetch origin                  # получить информацию об изменениях
```

`origin` и `gitlab` — это имена удалённых репозиториев. Они могут указывать на разные серверы.

Добавление удалённых репозиториев:

```bash
git remote add origin URL
git remote add gitlab URL
```

Изменение URL:

```bash
git remote set-url origin URL
```

</details>
## 6. Ветки (Branches)
<details>

```bash
git branch                       # показать локальные ветки
git branch feature               # создать ветку
git switch feature               # переключиться на ветку
git switch -c feature            # создать и переключиться
git merge feature                # объединить ветку с текущей
git branch -d feature            # удалить локальную ветку
```

</details>
## 7. Отмена изменений
<details>

```bash
git restore file.md              # отменить изменения в файле
git restore --staged file.md     # убрать файл из staging area
git commit --amend               # изменить последний коммит
git revert COMMIT_ID             # создать коммит, отменяющий другой
```

**Осторожно:** `git restore file.md` удаляет незакоммиченные изменения в этом файле. `git revert` обычно безопаснее для отмены уже опубликованных коммитов.
</details>
## 8. `.gitignore`
<details>
Файл `.gitignore` указывает Git, какие ещё не отслеживаемые файлы игнорировать.

Пример:

```gitignore
*.log
.env
__pycache__/
Drafts/
```

Проверить игнорирование:

```bash
git status
git check-ignore -v Drafts/notes.md
```

`.gitignore` не перестаёт отслеживать файлы, которые уже были добавлены в репозиторий.

</details>
## 9. Полезные команды
<details>

```bash
git show                         # показать последний коммит
git diff --stat                  # краткая сводка изменений
git log --oneline --graph --all  # история веток
git remote show origin           # информация об удалённом репозитории
git rm --cached file.md          # убрать файл из Git, оставив на диске
```

<details>
## 10. Типичный рабочий процесс
<details>

```bash
git status
git add Linux/permissions.md
git diff --cached
git commit -m "Update Linux permissions notes"
git push origin main
git push gitlab main
```

Добавляй только нужные файлы через `git add`, чтобы случайно не включить черновики в коммит.

</details>
## Запомнить
<details>

* `git add` — подготовить изменения.
* `git commit` — сохранить изменения в истории.
* `git push` — отправить коммиты.
* `git fetch` — получить сведения об изменениях на сервере.
* `git pull` — получить и интегрировать изменения.
* `git status` — проверить состояние.
* `git log` — посмотреть историю.

</details>

