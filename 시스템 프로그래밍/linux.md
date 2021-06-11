## 리눅스 (LINUX)
+ 서버에 많이 사용되는 운영체제
+ 최근 서버 환경은 주로 리눅스
+ 프로그래밍 할 때에도 많이 사용됨
+ 클라우드 컴퓨팅 (AWS)
+ UNIX 계열 운영체제
+ plain 하게 프로그래밍이 가능
  + ANSI C - C 언어 표준

### 리눅스와 파일
+ 모든 것은 파일이라는 철학을 따른다.
  + 모든 인터렉션은 파일을 읽고, 쓰는 것처럼 이루어져 있음
  + 마우스, 키보드와 같은 모든 디바이스와 관련된 기술도 파일과 같이 다루어진다.
+ 파일 네임스페이스
  + 전역 네임스페이스를 제공
    + windows = A 드라이브(A:/), C 드라이브(C:/) | Linux = /media/floofy/
+ 파일은 inode 고유값과 자료구조에 의해 주요 정보 관리

### 리눅스와 프로세스
+ 리눅스 실행 파일 포맷 - ELF(Executable and Linkable Format)
  + 콜스택, 코드(텍스트), 데이터 및 BSS 섹션 등
+ 다양한 시스템 리소스와 관련
  + 시스템콜 호출을 통해 리소스 처리 가능토록 구성
    + 타이머, 시그널, 파일, 네트워크, 디바이스, IPC 기법
+ 가상메모리 지원
+ 각 프로세스는 pid(프로세스 ID) 고유값으로 구분
+ init 프로세스(첫 번째 프로세스)를 기반으로 fork() 시스템 콜을 사용해서, 신규 프로세스가 생성

### 리눅스와 권한
+ 운영체제는 사용자/ 리소스 권한을 관리
+ 리눅스는 사용자/ 그룹으로 권한을 관리
+ root는 슈퍼 관리자
+ 파일마다 소유자, 소유자 그룹, 모든 사용자에 대해 읽고, 쓰고, 실행하는 권한을 관리
  + 접근 권한 정보는 inode의 자료구조에 저장

## 쉘(Shell)
+ 사용자와 컴퓨터 하드웨어 또는 운영체제간 인터페이스
  + 사용자의 명령을 해석해서, 커널에 명령을 요청해주는 역할
  + 관련된 시스템콜을 사용해서 프로그래밍이 작성되어 있다.
+ 종류
  + Bourne-Again Shell(bash) : GNU 프로젝트의 일환으로 개발, 리눅스의 디폴트
  + Bourne Shell (sh)
  + C Shell (csh)
  + Korn Shell (ksh) : 유닉스에서 가장 많이 사용됨
+ bash 명령어
  + 다중 사용자 관련 명령어
    + whoami : 로그인한 사용자 ID를 알려줌
    + passwd : 로그인한 사용자 ID의 암호 변경
    + useradd : 사용자 기본 설정 자동으로 하지 않음
    + adduser : 사용자 기본 설정을 자동으로 수행
    + sudo : root 권한으로 실행하기
    + su : 사용자 변경
      + su root : 현재 사용자의 환경설정 기반 root로 변경
      + su - root : 변경되는 사용자의 환경설정을 기반으로, root로 전환
  + 파일 및 권한 관리 명령어
    + pwd : 현재 디렉토리 위치
    + cd : 디렉토리 이동
    + ls : 파일 목록 출력
      + * : 임의의 문자열
      + ? : 문자 하나
    + man : manual 명령어
    + chmod : 파일 권한 변경
      + 기호 문자를 사용하는 방법     
        ![image](https://user-images.githubusercontent.com/74183179/120466782-6e8db680-c3da-11eb-9688-ccb77c297010.png)
      + 숫자를 사용하는 방법     
        ![image](https://user-images.githubusercontent.com/74183179/120466830-7baaa580-c3da-11eb-9338-7b0ac61684f3.png)
        
    + chown : 소유자 변경
      + chown [옵션] [소유자:소유자그룹] [파일]
      + ex) chown root:root file / chown root: file / chown :root file
    + chgrp : 소유자 그룹 변경
      + chgrp [옵션] [그룹] [파일]
      + ex) chgrp -R root directory
    + cat : 파일 보기
    + head : 파일 시작 부분 보기
    + tail : 파일 끝 부분 보기
    + more : 파일 보기 (화면을 넘기면서 볼수 있음)
    + rm : 파일 및 폴더 삭제
      + r : 하위 디렉토리를 포함한 모든 파일 삭제
      + f : 강제로 파일이나 디렉토리 삭제

        
### ls와 파일 권한
+ 파일마다 소유자, 소유자 그룹, 모든 사용자에 대해 읽고, 쓰고, 실행하는 권한 설정 (소유자 접근 권한 정보는 inode에 저장)
+ 사용자
  + 소유자 : 소유자에 대한 권한
  + 그룹 : 소유자가 속해 있는 그룹에 대한 권한
  + 공개 : 모든 사용자들에 대한 권한
+ 퍼미션 종류
  + 읽기(r) : 읽기 권한
  + 쓰기(w) : 쓰기 권한
  + 실행(x) : 실행 권한

  ![image](https://user-images.githubusercontent.com/74183179/120330094-72143580-c327-11eb-83d1-b0a2b7c5146a.png)
  
  
## Standard Stream (표준 입출력)
+ command 로 실행되는 프로세스는 세 가지 스트림을 가짐
  + 표준 입력 스트림 (Standard Input Stream) - stdin
  + 표준 출력 스트림 (Standard Output Stream) - stdout
  + 오류 출력 스트림 (Standard Error Stream) - stderr
+ 모든 스트림은 일반적인 plain text로 console에 출력하도록 되어있음


## 리다이렉션 (redirection)
+ 표준 스트림 흐름을 바꿔줄 수 있다.
  + > , < 을 사용
  + 주료 명령어 표준 출력을 화면이 아닌 파일에 쓸 때      
+ ex) ls > files.txt
  + ls로 출력되는 표준 출력 스트림의 방향을 files.txt로 바꿔줌 (ls출력결과가 files.txt에 저장)
+ ex) head < files.txt
  + files.txt의 파일 내용이 head라는 파일의 처음부터 10라인까지 출력해주는 명령으로 넣어짐 (files.txt의 앞 10라인이 출력)
+ ex) head < files.txt > files2.txt
  + files.txt의 파일 내용이 head로 들어가서, files.txt의 앞 10라인 출력
  + head의 출력 스트림은 다시 files2.txt로 들어감
  + head는 files.txt 내용을 출력하지 않고 출력 내용이 files2.txt에 저장 (결과적으로 files.txt의 앞 10라인이 files2.txt에 저장)
+ ex) ls >> files.txt
  + 기존에 있는 files.txt파일 끝에 ls출력 결과를 추가
   
   
   ![image](https://user-images.githubusercontent.com/74183179/120467709-684c0a00-c3db-11eb-913a-79591be3cfdb.png)
   
## 파이프 (pipe)
  + 두 프로세스 사이에서 한 프로세스의 출력 스트림을 또다른 프로세스의 입력 스트림으로 사용할 때 사용
  + ex) ls | grep file
    + ls 명령을 통한 출력 내용이 grep 명령의 입력 스트림으로 들어감
    + grep file는 grep명령의 입력 스트림을 검색해서 file이라는 문구가 들어 있는 입력 내용만 출력      
     ![image](https://user-images.githubusercontent.com/74183179/120468442-325b5580-c3dc-11eb-96de-b008b261b6df.png)     
     ![image](https://user-images.githubusercontent.com/74183179/120468476-3be4bd80-c3dc-11eb-9024-cf6b04b2fab7.png)

     

## 프로세스 vs 바이너리
+ 코드 이미지 또는 바이너리 : 실행파일
+ 실행 중인 프로그램 : 프로세스
  + 가상 메모리 및 물리 메모리 정보
  + 시스템 리소스 관련 정보
  + 스케줄링 단위

## foreground process / background process
+ foreground process : 쉘에서 해당 프로세스 실행을 명령한 후, 해당 프로세스 수행 종료까지 사용자가 다른 입력을 하지 못하는 프로세스
  + CTRL + z : foreground process 실행 중지 상태 (suspend 모드)로 변경
  + 맨 마지막 CTRL + z로 중지된 프로세스는 bg명령으로 background 프로세스로 실행될 수 있음
  + jobs 명령어 : 백그라운드로 진행 또는 중지된 상태로 있는 프로세스를 보여줌
  + CTRL + c : 프로세스 작업 취소
+ background process : 사용자 입력과 상관없이 실행되는 프로세스
  + 쉘에서 해당 프로세스 실행시, 맨뒤에 &를 붙여줌
  + ex) find / -name '*.py' > list.txt &
 
## 프로세스 상태 확인 (ps)
+ ps [options]
+ options    
  ![image](https://user-images.githubusercontent.com/74183179/120638656-5afe5080-c4ab-11eb-9c92-e5996f8c7652.png)
+ 데몬 프로세스 (daemon process) : daemon은 악마를 의미. 사용자 모르게 시스템 관리를 위해 실행되는 프로세스로 보통 시스템이 부팅될 때 자동실행

## 리눅스 파일 구조
![image](https://user-images.githubusercontent.com/74183179/121010910-f441a580-c7d0-11eb-9edd-b4cbc8c3631e.png)

## 하드 링크, 소프트 링크
+ cp명령 : 파일 복사
  + 10MB 사이즈를 가지고 있는 A파일을 B파일로 복사
    + cp A B -> A와 B는 각각 물리적으로 10MB 파일로 저장
+ 하드 링크 : ln A B
  + A와 B는 동일한 10MB 파일을 가르킴
  + 동일한 파일을 가진 이름을 하나더 만든 것
    + inode 동일
    + 전체 파일용량 동일
  + rm A로 A를 삭제하면 B파일 접근 가능
  + A파일 수정시 B파일도 동일한 수정
  
+ 소프트 링크 : ln -s A B
  + Windows OS의 바로가기와 동일
  + rm A로 A를 삭제하면 B파일 접근 불가
  + A파일 수정시 B파일도 동일한 수정


## 특수 파일
  + 디바이스
    + 블록 디바이스 (Block Device)
      + HDD, CD/DVD와 같이 블록 또는 섹터 등 정해진 단위로 데이터 전송, IO송수신 속도 빠름
    + 캐릭터 디바이스 (Character Device)
      + 키보드, 마우스 등 byte단위 데이터 전송, IO 송수신 속도가 느림

## API
+ 응용 프로그램과 분리된 하위 호환 인터페이스 (시스템 콜 래퍼, 입출력 라이브러리)


## C 라이브러리, C 컴파일러
+ 유닉스 C 라이브러리 / 컴파일러 - libc / cc
+ 리눅스 C 라이브러리 / 컴파일러 - GNU libc-glibc / GNU cc- gcc

## ABI
+ 응용 프로그램 바이너리 인터페이스
+ 함수 실행 방식, 레지스터 활용, 시스템 콜 실행, 라이브러리 링크 방식 등
+ ABI가 호환되면 재컴파일 없이 동작
+ 컴파일러, 링커(라이브러리 링크), 툴체인 (컴파일러를 만드는 프로그램) 에서 제공

## POSIX
+ 유닉스 시스템 프로그래밍 인터페이스 표준
+ IEEE(Institute of Eletronic and Electronics Engineers)에서 표준화 시도
+ 리차드 스톨만이 POSIX를 표준안 이름으로 제안

## C 언어 표준
+ 다양한 C언어 변종
+ ANSI(American National Standards Institute)에서 ANSI C 표준 정립
> 리눅스는 POSIX와 ANSI C지원  

## 프로그램, 프로세스, 그레드
+ 프로그램 : 바이너리, 코드 이미지, 응용프로그램. Application, 또는 실행파일
+ 프로세스 : 실행중인 프로그램 (메모리 적재 + 프로세스 상태 정보 포함)
+ 스레드 : 
  + 리눅스 프로세스는 기본 스레드 포함
  + 싱글스레드 프로세스 : 기본 프로세스
  + 멀티스레드 프로세스 : 여러 스레드 존재

## 프로세스 ID
+ pid, 각 프로세스는 해당 시점에 unique한 pid를 가짐
+ pid 최대 값은 32768
+ 부호형 (signed) 16비트 정수값 사용

## 프로세스 계층
+ 최초의 프로세스 : init 프로세스, pid 1
+ init 프로세스는 운영체제가 생성
+ 다른 프로세스는 또 다른 프로세스로 부터 생성
  + 부모 프로세스, 자식 프로세스
+ ppid 값이 부모 프로세스의 pid를 뜻함
  + ps -ef 명령어를 통해 ppid 확인 가능 
  + -e 시스템상의 모든 프로세스 출력, 
  + -f 다음 목록 출력(UID, PID, PPID, CPU%, STIME, TTY, TIME, CMD

## 프로세스와 소유자 관리
+ 리눅스 내부에서는 프로세스의 소유자(사용자)와 그룹을 UID/GID로 관리
+ 사용자에 보여줄때에만 UID와 사용자 이름 매핑 정보를 기반으로 사용자 이름으로 제공

## 프로세스 생성
+ 기본 프로세스 생성 과정
  1. TEXT, DATA, BSS, HEAP, STACK의 공간 생성
  2. 프로세스 이미지를 해당 공간에 업로드 하고 실행 시작
+ 프로세스 계층 : 다른 프로세스는 또 다른 프로세스로부터 생성

## fork() / exec() 시스템 콜
+ fork() - 복사
  + 새로운 프로세스 공간을 별도로 만들고, fork() 시스템콜을 호출한 프로세스 공간을 모두 복사
    + 별도의 프로세스 공간을 만들고, 부모 프로세스 공간의 데이터를 그대로 복사
  + 자식 프로세스는 pid 0으로 리턴, 부모 프로세스는 실제 pid 리턴
  + 두 프로세스의 변수 및 PC는 동일
  + 새로운 프로세스 공간을 별도로 만들고, fork() 시스템 콜을 호출한 프로세스 공간ㅇ르 모두 복사한 후, fork() 시스템 콜 이후 코드 부터 실행
+ exec() - 덮어씌움
  + exec() 시스템콜을 호출한 현재 프로세스 공간의 TEXT, DATA, BSS영역을 새로운 프로세스의 이미지로 덮어 씌움
    + 별도의 프로세스 공간을 만들지 않음
  + exec() suffix
    + l : 실행파일에 전달할 인자를 List로 전달함. 함수에 가변 인자로 전달되며 그 끝은 (char *) NULL을 마지막으로 전달해 표시.
    + p : 실행할 파일이 (file 파라미터)가 ‘/’로 시작하지 않는 경우 PATH 환경변수에 명시된 경로에서 실행파일을 찾음.
    + e : 새로운 프로세스 이미지가 사용할 환경변수를 설정함. 환경변수는 null-terminated string의 array로 표현되며 array 포인터를 인자로 전달함. Array의 끝은 NULL 포인터를 사용하여 표시.
    + v : 실행파일에 전달할 인자를 vector로 전달함. Vector는 null-terminated string의 array의 포인터로 전달.Array의 끝은 NULL 포인터를 사용하여 표시
    














    

