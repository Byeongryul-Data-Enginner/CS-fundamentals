# 터미널 기초 사용법
## 유튜브 영상과 정리된 글을 합쳐서 정리함
### 작성자: 이병률
Content
1. [메뉴얼, 도움, 청소](#메뉴얼,-도움,-청소)
2. [파일 시스템 탐색](#파일-시스템-탐색)
3. [파일 생성 및 관리](#파일-생성-및-관리)
4. [환경 변수 설정](#환경-변수-설정)
5. [참고 사이트](#참고-사이트)
---
## 메뉴얼, 도움, 청소
### **man**ual
우리는 새로운 도구를 샀을 때, 그 도구의 메뉴얼을 읽어본다. 터미널도 메뉴얼을 제공한다.
<pre>
~$ man <궁금한 명령어>
</pre>
다음과 같은 방법으로 명령어를 찾을 수 있다. 이 방법을 통해 명령어의 정보를 확인 했다면, **"q"** 를 통해 다시 터미널로 돌아와야한다.

이 방법을 사용하지 않고 명령어를 알아보는 방법은 도움을 요청하는 것이다.
### **h**elp
<pre>
~$ <궁금한 명령어> -h
~$ <궁금한 명령어> --h
~$ <궁금한 명령어> -help
~$ <궁금한 명령어> --help
</pre>
"-"는 명령어에 속해있는 추가적인 설정으로 보통 "h"는 사용법을 출력하게 되어있다.

위 명령어를 사용하면 명령어 사용법이 길게 서술되어 있는데 이때, 화면을 청소하는 명령어를 사용하면 좋다.
### **clear**
<pre>
~$ clear
</pre>
상단에 나열되어 있던 모든 요소가 지워질 것이다.

---
## 파일 시스템 탐색
먼저 나 자신의 위치를 파악해보자.
### **p**rint **w**orking **d**irectory
<pre>
~$ pwd
/User/Byeongryul/
</pre>
현재 작업중인 폴더(이후 디렉토리)를 보여준다.

내 위치를 확인했으니 주변를 둘러보자.
### **l**i**s**t
<pre>
~$ ls
dir file
~$ ls -a
. .. dir file
~$ ls -l
drwxrwxrwx 1 Byeongryul Byeongryul 4096 Seq 7 11:11 dir
-rwxrwxrwx 1 Byeongryul Byeongryul    0 Seq 7 11:11 file
~$ ls -al
drwxrwxrwx 1 Byeongryul Byeongryul 4096 Seq 7 11:11 .
drwxrwxrwx 1 Byeongryul Byeongryul 4096 Seq 7 11:11 ..
drwxrwxrwx 1 Byeongryul Byeongryul 4096 Seq 7 11:11 dir
-rwxrwxrwx 1 Byeongryul Byeongryul    0 Seq 7 11:11 file
</pre>
주변을 둘러보는 방법은 여러가지가 있다. 단순이 둘러보거나, 숨은 것 까지 확인하거나(-a), 하나하나 꼼꼼하게 볼 수 있다.(-l) 그런 요소를 합쳐서 처리할 수 도 있다.(-la or -al)

여기서 "."은 현재 디렉토리를 의미한다. ".."은 상위 디렉토리를 의미한다.

그럼 주변을 둘러봤으니 이동해보자.

### **c**hange **d**irctory
<pre>
~$ cd dir
~/dir$ cd ..
~$ cd -
~/dir$ cd ~
~$ cd /User/Byeongryul/dir
~/dir$ cd
~$ cd
</pre>
내 디렉토리에서 "dir"로 이동할 수 있고,(cd dir) 내 디렉토리에서 상위 디렉토리로 이동할 수 있으며,(cd ..) 이전에 작업하던 디렉토리로 이동할 수 있고(cd -), 홈 디렉토리로 이동할 수 있으며(cd or cd ~), 정확하게 지정한 디렉토리로 이동할 수 있다.(cd /User/Byeongryul/dir)

정확하게 지정한 디렉토리 이동을 **절대경로**라고 말하고 내 디렉토리에서 이동한다 라고 하면 **상대경로** 라고 이야기한다. 이러한 경로 지정은 ls 명령어에도 사용할 수 있다.

우리는 이제 CLI 환경에서 자유롭게 이동할 수 있게 되었다. 하지만 다른 사람의 프로젝트를 확인하는 능력을 얻기 위해서 내가 원하는 디렉토리나 파일이 어디있는지 알아 내야한다. 이때 사용하는 명령어가 **find** 이다.
### **find**
<pre>
~$ find
.
./file
./dir
~$ find . -type f -name "*"
./file
~$ find . -type d -name "*"
.
./dir
</pre>
find에 아무런 설정을 하지 않으면 모든 요소를 나열하게 된다. 하지만 정확하게 어떤 type인지 서술하고 이름까지 나열한다면 원하는 폴더와 파일을 찾아낼 수 있을 것이다.

## 파일 생성 및 관리
위 행동을 통해 프로젝트 안에서 자유롭게 움직일 수 있게 됐다면, 다음으로 파일을 만들어 보자!
### **touch**
<pre>
~$ touch new-file
</pre>
왜 명령어 이름이 "touch"일까? 원래 touch는 서류가 제작된 시간을 바꾸기 위해 사용되는 명령어 였다. 하지만 이 명령어를 사용하면 없는 파일을 만들어주기 때문에 이 명령어를 사용하게 되었다.

"new-file"이라는 파일을 만들었다. 만든 파일의 내용을 보기 위해서는 다른 명령어가 필요하다.
### con**cat**enate(연결?)
<pre>
~$ cat file
Hello World!
~$ cat file new-file
Hello World!
~$ tail -n1 file
Hello World!
~$ head -n1 file
Hello World!
</pre>
"cat"을 통해 파일 내부 내용을 확인 할 수 있고 여러 파일을 동시에 열어볼 수 있다.

끝에서 부터 10줄까지 확인하거나(tail) 앞에서 부터 10줄까지 확인할 수 있다.(head) 수를 추가하면 그만큼 출력된다.

만약 입력된 문자열을 그대로 출력하고 싶으면 어떻게 할까? 메아리 처럼..

### **echo**
<pre>
~$ echo Hello!
Hello!
</pre>
말 그대로 입력한 값을 출력한다! 하지만 이것을 효과적으로 사용하기 위해서는 환경변수와 지역변수 등을 알아야 쉽게 사용할 수 있다.. 이는 [다음](#환경-변수-설정)을 참고하자.

만약 echo나 find.. ls 같은 출력값을 파일에 저장하고 싶으면 어떻게 해야할까?
### **> or >>**(리다이렉트)
<pre>
~$ ls -al > ls.txt
~$ ls -l > ls.txt
~$ ls -al >> ls.txt
</pre>
">" 는 파일을 덮어 써서 저장하고 ">>"는 원본 내용에서 추가한다. 과거부터 현재까지 결과를 알고 싶다면 반복적으로 수집하면 될 것으로 생각된다.

이렇게 저장한 파일들은 다시 알맞은 디렉토리에 나누어 저장하면 좋다. 그러면 디렉토리는 어떻게 만드는가?
### **m**a**k**e **dir**ctory
<pre>
~$ mkdir new-dir
~$ mkdir -p 1/2/3
</pre>
"new-dir"라는 새로운 디렉토리가 생성되었다. 만약에 만들어지지 않은 디렉토리 안에 디렉토리를 만들고 싶으면 "-p"를 추가하면 자동으로 생성된다.

자 이제 새로만든 파일을 어떻게 새로 만든 디렉토리에 넣을까?
### **c**o**p**y & **m**o**v**e & **r**e**m**ove
<pre>
~$ cp new-file save-file
~$ mv new-file new-dir
~$ cp -r new-dir save-dir
~$ rm save-file
~$ rm -r save-dir
</pre>
혹시 명령어를 잘못 사용하여 파일이 날아 갈 수 있으니 "save-file"을 만들어 복사한다.

이후 옮길 파일명, 옮겨질 디렉토리나 파일을 입력하면 이동하게 된다.

만약, 디렉토리를 복사하고 싶으면 어떻게 해야할까? 이떄는 "-r"를 추가하여 내부까지 함께 복사한다고 명시하면 된다.

완벽하게 복사가 됐다면 백업파일을 지워주자. 여기서 폴더를 지우는 방법도 동일하다.

파일의 이름은 모르지만 알고싶은 내용을 검색하는 방법을 알아보자.
### **g**lobal | **r**egular **e**xpression | **p**rint
<pre>
~$ grep hello file
hello
~$ grep -n hello file
2:hello
~$ grep -i hello file
hello
Hello
~$ grep -r hello .
./new-dir/new-file:hello
./new-file:hello
</pre>
명령어, 설정, 파일 또는 디렉토리 이름을 설정하면 다음과 같이 출력된다. 물론 설정은 중복하여 설정할 수 있다.

마지막으로 변수의 사용이다.

---
## 환경 변수 설정
현재 선언된 환경변수를 볼 수 있다. 또 생성하고 사용하고 제거할 수 있다.
<pre>
~$ env
~$ export DIR_LOCATE=dir
~$ echo $TEST_DIR
dir
~$ unset TEST_DIR
</pre>
단순 변수를 원한다면 "a=dir" 이라고 해주면 된다. 사용은 환경변수와 동일하다.

---
## 이외 더 배우고 공부해야하는 명령어들
### vim
### ps
### whoami
### sleep
### fg
### bg
### jobs
### kill
### history
### !
### Tab, ctrl + z, c, d 등등
## 참고 사이트

**[글 내용이 방대한 분량](https://www.44bits.io/ko/post/linux-and-mac-command-line-survival-guide-for-beginner)**

**[영상 이 글에 큰 토대를 따라감 총 15가지 명령어를 다룸](https://www.youtube.com/watch?v=EL6AQl-e3AQ)**