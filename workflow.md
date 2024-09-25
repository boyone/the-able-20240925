# 1. การจัดการและบริหาร Source Code เบื้องต้น ส่วนที่ 1

## 1. Workflow ของ Git

![Workflow](./images/lifecycle.png)

## 2. Basic Commands ที่ใช้ประจำ

- git init
- git clone
- git status
- git status --short
- git diff
- git add
- git commit
- git commit -m "Commit message"
- git log
- git log --oneline
- git log --oneline --graph
- git log --stat
- git mv
- git rm
- git reset: --soft, --mixed, --hard
  - git reset --soft
  - git reset --mixed
  - git reset --hard

## 3. setup git

- git config

  ```sh
  git config list
  git config list --global
  git config list --local
  ```

  1. pull.rebase=false

     1. local

        ```sh
        git config set --local pull.rebase false
        git config set pull.rebase false
        git config unset --local pull.rebase
        git config unset pull.rebase
        ```

     2. global

        ```sh
        git config set --global pull.rebase false
        git config unset --global pull.rebase
        ```

  2. core.ignorecase=false

     1. local

        ```sh
        git config set --local core.ignorecase false
        git config set core.ignorecase false
        git config unset --local core.ignorecase
        git config unset core.ignorecase
        ```

     2. global

        ```sh
        git config set --global core.ignorecase false
        git config unset --global core.ignorecase
        ```

## 4. gitignore

```.gitignore
# dotenv files
.env

# Build results
[Dd]ebug/
[Dd]ebugPublic/
[Rr]elease/
[Rr]eleases/
x64/
x86/
[Ww][Ii][Nn]32/
[Aa][Rr][Mm]/
[Aa][Rr][Mm]64/
bld/
[Bb]in/
[Oo]bj/
[Ll]og/
[Ll]ogs/
```

## 5. getting help

1. git help <verb>
2. git <verb> help
3. man git-verb
