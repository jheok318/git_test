Git & Git hub
=======================

## github의 시작

1. 계정을 생성해준다

2. 계정을 생성후 repository를 생성해주면 code부분에 setup을 하는 방법이 나와있다

<hr/>
## Git의 Gitbuh 자동 로그인 

1. 이중 ssh를 이용하여 매번 git push를 할때 아이디 비밀번호를 입력할 필요 없게 설정을 해준다

2. ssh-keygen -t rsa -C "cfd0318@gmail.com" 를 입력해주면 rsa key를 얻을수 있다.

3. 
```
   $ ssh-keygen -t rsa -C "cfd0318@gmail.com"
   Generating public/private rsa key pair.
   Enter file in which to save the key (/c/Users/mobigen/.ssh/id_rsa):
   Enter passphrase (empty for no passphrase):
   Enter same passphrase again:
   Your identification has been saved in /c/Users/mobigen/.ssh/id_rsa
   Your public key has been saved in /c/Users/mobigen/.ssh/id_rsa.pub
   The key fingerprint is:
   SHA256:Awi8VosyvulVk602I7pStXg4fS86jJnb6BtJSLdmBSs cfd0318@gmail.com
   The key's randomart image is:
   +---[RSA 3072]----+
```
4. /c/Users/mobigen/.ssh/id_rsa에 id_rsa가 생성되었다.

5. 이 파일의 긴 문자열을 github의 올리려고 햇던 저장소의 setting메뉴 Deploy keys에 추가로 등록을 해준다

6. 이후에 add, commit, push를 통해 github에 파일을 저장할수 있다.

<hr/>

## Git에서 자주 쓰이는 용어의 개념 및 사용법

![image-20200625170853291](/img/add.png)

###### _Remote Repository에는 README.md 파일만 있다고 가정_

+ **init**
+ 깃 저장소를 초기화한다. 저장소나 디렉토리 안에서 이 명령을 실행하기 전까지는 그냥 일반 폴더이다.

```
  git init
```

+ **status**

  + 저장소의상태를 체크하며 어떤 파일이 저장소에 있고 커밋이 필요한 변경사항이 있는지, 현재 저장소의 어떤 브랜치에서 작업하고 있는지 등을 확인 할수 있다.

```
  git status
```

+ **add**

  - add명령어로 repository에 새 파일들을 추가 하지는 않는다.
  - 대신 깃이 새파일들을 주시하게 해준다.
  - Working Directory에 있는 README.md를 Staging Area에 보내준다.
```
  git add README.md
```

+ **commit**

  + 어떤 변경사항이 생겼다면 repository의 스냅샷을 찍기 위해 입력을 해준다.
  + Staging Area에 있는 README.md를 Local Reository에 보내준다.

```
  git commit -m "first commit"
```

  + 이때까지 하나의 commit이 버전의 구분점이 되며 이전 버전에서 해당 버전으로의 변경내역이 local 저장소에 담겨 있다. 이는 모두 local에서 작동한다.

+ **push**

  + Local Repository에 있는 README.md를 Remote Repository로 올려준다.
  + git push를 통해 remote 저장소에 commit을 올려준다.
```
  git push 
```

+ **pull**

  + Remote Repository에 있는 README.md를 Remote Repository로 올려준다.
  + origin repository에서 변경 사항을 가져와 현재 branch에 합친다.

```
  git pull
```

+ **branch**

  ![image-20200625173627537](/img/branch.png)
  
  + 여러 사람과 작업하고 자신만의 작업을 원할때 즉, 독립적 작업을  할 때 사용한다.
  + 새로운 브랜치를 만들고 자신만의 변경사항등의 커밋 타임라인을 만든다.
  + 동시에 여러 작업을 진행할 수 있다.
  + 이렇게 동시에 작업한 branch들을 나중에 merge할 수 있다.
  + newbranch라는 새로운 branch를 생성한다.

```
  git branch newbranch
```

+ **Master branch**
+ Master branch란 처음 저장소를 만들 때 생성되는 branch
  + 새로운 파일을 추가하거나 변경 시 그 내용을 저장하는 곳은 모두 master branch를 통해 merger한다.
  
+ **merge**

  + 브랜치에서 작업을 끝내고, 모든 협업자가 볼수 있는 master 브랜치로 병합한다.

```
  git merge
```

+ **clone**

  + remote repository를 local repository로 복제할때 사용한다

```
    git clone https://github.com/jheok318/git_test
```

+ **log**

  + 현재 git에서 일어난 모든 이력을 확인 한다.

```
  git log
```

+ **fork**

  + Fork를 통해 다른 사람의 repository를 가져와 내 repository를 만든다.
  + 이후 git clone으로 내 repository에 있는 파일들을 Working  Directory로 가져온다.
  + 이 clone으로 가져온 파일에서 add, commit을 하여도 원본 저장소에는 영향이 없다.

+ **Pull Request**

  + 내 저장소에서 add, commit, push를 한 후에 원본 저장소에 이 작업을 반영해달라고 요청하는 것이 Pull Request이다.

<hr/>

## Git commit  message의 규칙 및 사용시 도움이 될만한 것들

1. 제목과 본문을 빈행으로 분리한다.

   + 필수 사항은 아니다.
   + 한줄만 작성해도 괜찮은 경우들이 존재한다.
   + 제목과 본문 사이에 공백을 넣으면 로그를 확인 할때 어떤 경우라도 제목과 본문을 출력해준다.

```
$ git log --oneline
59e2bf2 (HEAD -> master, origin/master) README.md or imgfile
05eab6e README.md
37866b9 README.md

$ git shortlog
jun_heok (3):
      README.md
      README.md
      README.md or imgfile
```


2. 제목 행을 50자로 제한한다.

   + 제목 행을 50자로 작성하는 것은 강제로 제한 하는것은 아니다.
   + GitHub UI는 50자 이상을 입력하려고 하면 경고 표시가 나타난다.
   + ![image-20200626091824456](img/commit50.png)

3. 제목 행 첫 글자는 대문자로 쓴다

   + 제목 행에서의 모든 단어는 대문자로 시작함을 생각하자
   + readme.md file change.  =>  Readme.md file change.

4. 제목 행에 명령문을 사용한다.

   + 명령이나 설명하듯 제목 행을 작성해준다.
   + Git 자체는 우리 대신 자동으로 커밋을 생성하는 경우, 명령조로 사용을 한다.
   + 이는 제목 행에서만 생각을 하며 본문을 쓸때는 생각할 필요 없다.
   + Readme.md file change. => Change readme.md file.

5.  제목 행 끝에 마침표를 넣지 않는다.

   + 제목 행 끝에는 마침표가 필요없다. 50자 미만의 규칙을 따르면 한 공간도 필요로 하다.
   + Change readme.md file. => Change readme.md file

6. 본문은 72자 기준으로 개행한다.

   + Git은 본문을 자동으로 개행하지 않는다.
   + 커밋 메세지 본문을 적을 땐 본문 우측 여백을 신경쓰며 작성해야 하고, 본문을 정해진 대로손수 개행 해야 한다
   + 72자 기준으로 개행을 하면 전체 80자 공간중 Git이 들여쓰기 문자를 위해 여유 문자를 가질 수 있다.

7. 어떻게 보다 무엇과 왜를 쓴다.

   + 대부분은 어떻게 바뀌었는지를 남긴다.
   + 하지만 왜 바꾸었는지에 주목을 해보면 바꾸기전에 무엇을 했는지(무엇이 잘못 동작 했는지)
   + 지금은 어떻게 동작하는지 그리고 왜 그렇게 바꾸기로 했는지를 중점적으로 적어주는 것이 좋다.

<hr/>

issue1


issue2 입력











