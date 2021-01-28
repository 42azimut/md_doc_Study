## 리눅스 명령어 
### [시골사는개발자 유튜브 참고](https://www.youtube.com/watch?v=9_KIdQ8abH4)

___ 
1) pwd, ls
- pwd : present working directory
- ls : file, diretory list

- `ls -l`
- `ls -al` (숨김파일 포함 디렉토리, 파일 리스트)

2) chmod (change mode) : 권한수정 
          user group other
- file : - rwx rwx rwx
- dir  : d rwx r-x r-x
- link : l rwx r-- ---

```
# 비트연산
# 모두 실행권한 제거
chmod 664 a.out

# 유저모두가능 그룹(실행만제거) 다른(읽기만)
chmod 764 a.out
```
___
3) mkdir / touch / rm 
```
- mkdir : 디렉토리 생성
- touch filename.c (빈파일 생성)
- rm -f : 파일 지울때 -f 옵션
- rm -r : 폴더 지울떄 -r 옵션
```
___
4) cd (change directory)
```
/    #절대위치 기준
./   #현재위치 
../  #현재위치 상위
~/   #Home위치 기준
```
___
5) mv (move : 이동 및 이름변경)
```
 <mv source destination>
 mv a.out b.out #이름 변경
 mv b.out ./dir2/. #폴더 이동
```
___
6) cp (copy)
```
<cp source dstination>
cp file2 file2
cp file2 ./dir2/myfile2

# **디렉토리 복사 -r 옵션 *****
cp -r dir1 dir3
```
___
7) link (hard link & soft(symbolic) link)
link file  & filesytsem(물리적_하드디스크 위치)
1) soft link
- 흔히 알고 있는 링크이다. (복사본 없음) // inode(고유번호)
- link file 파일명에는 반드시 inode가 있고, 파일시스템(file system)의 inode에 연결(링크)되어 있다.
- 파일시스템의 Ref는 링크파일의 개수이다. 즉 파일이 한개 생성되면, ref는 1 이다.

2) hard link
- 링크 파일에서 조별과제발표.ppt 와 팀발표자료.ppt 두개의 복사본 파일이 있다고 가정. inode==3 이라 하자. 그렇다면 파일시스템의 inode==3 역시 같고, Ref 값만 2 이다. 
같은 파일(복사된) 두개의 링크파일이 한개의 파일시스템의 3번 inode를 가리키고(참조) 있기 때문이다. 
- 링크파일의 복사본중 한개의 파일을 삭제 하면, 파일시스템의 inode 3을 찾아가서 Ref 값 2-1 = 1이 된다.
- 따라서 링크파일에 여전히 1개의 파일이 연결되어 있다는 의미!  
- 폴더에는 하드링크를 설정할수 없다. 파일만 가능! (소프트링크는 폴더도 가능)

 
```
- 소프트 링크 연결하는 방법
ln -s source target   # -s  옵션은 의미는 소프트 링크
touch library.0.1.so   #파일 생성
ln -s library.0.1.so library.so  #링크연결
library.so -> library.0.1.so #연결된 링크 확인
touch library.0.2.so  #새로운 파일 생성
rm -f library.so  #링크 원본 삭제
ln -s library.0.2.so library.so
library.so -> library.0.2.so  # 링크 안됨! 위에서 삭제 했기 때문에.쓰레기 파일!

- 하드링크
ln source target  #옵션 없이 사용!
ex)
touch file1
ln file1 myfile

ls -li
8794432 -rw-r--r--  2 azimut_mac  staff     0 Jan 28 19:25 file1
8794432 -rw-r--r--  2 azimut_mac  staff     0 Jan 28 19:25 myfile

rm -f file1 #원본 파일을 삭제 해도 복사된 myfile1 영향 없음!

ls -li
8794432 -rw-r--r--  1 azimut_mac  staff     0 Jan 28 19:25 myfile
```
___
8) cat  "concatenate" ==> 표준입력을 표준출력으로 
```
# | 파이프라인(pipeline)
cat fileName | more   

# > 꺽쇠(Redirection)
cat source > target

# 복사하여 출력
cat test00.c > test01.c  #주의 test01.c 이미 존재하면 덮어쓰임!

# 이미 존재 하는 파일내용 하단에 이어 붙여서 출력하기 
cat test00.c >> test01.c
```
___
9) head  or tail
- 첫줄 몇라인만 출력하기
```
head test.c
```
- **** 중요! 마지막 몇 라인만 출력하기  *****
```
tail -f filename  # -f 옵션은 화면에 마지막에 새로운게 추가되면 화면에 바로 출력하게 할수 있다.

ex)
tail -f system.log

# 새로운 터미널 창에서
echo "error message!" >> system.log   
```
___
10) grep 문자열 파일이름 
#검색 단어를 문자열을 찾아주는 명령어!
```
grep test *.log

# -H 옵션
grep -H test *.log  # -H 파일 이름까지 출력

grep -Hw test1 *.log  # -w 옵션은 정확히 일치하는 "test1"와 같은 문자열을 찾는다!
 ```
___
11) less 명령어
- 화면에 일부만 출력. 용량이큰 파일을 읽을때는 less 명령어를 사용해야 한다! 
- 예를들어 1gb 짜리 system.log 를 vi system.log 오픈하면 작살남!
- `less system.log`  # 파일 일부만 오픈!
___
12) tar 명령어 : 파일 압축 또는 압축 풀기
```
- 압축하기  cvfz 옵션
- cvfz 옵션 : create(압축생성)
`tar cvfz backup.tar.gz ./dir3 ./file3 ./system.log 

- 압축풀기 xvfz 옵션
`tar xvfz filename`
```
___
13) root 계정
```
sudo
```
___

14) chown 
- root권한이 필요 sudo 명령어 사용!

`sudo chown user:group target_file(dir)`

`sudo chown dust:dust test01.c`
___
15) find  
- 검색 옵션이 대단히 많다! (최근변경된 파일, 생성시간기준, 파일크기, 링크파일여부, inode번호, user/group권한별, 파일유형, 파일 이름......)

`find 경로 조건 target`

`find . -name system.log`
___
16) which  
- 명령어의 위치를 찾아주는 which 명령어

`which python3`
___
16) top
___
17) who
- 현재 리눅스 장비에 접속한 사람이 누군지 확인!
___
18) ping
- ping domain

`ping google.com`
___
19) nslookup
- 도메인주소의 ip넘버(주소)를 알려줌!

`nslookup`
___
20) ps (process state)
- 모든 프로세스의 상태를 표시!

`ps -ef`  

- 필요한 프로세스만 골라서 확인할떄

`ps -ef | grep a.out`
___
21) kill 
- 해당 프로세스를 강제 종료!
- -9 옵션 이다!! 
`kill -9 process.id`   

`kill -9 11134`
___
22) adduser
- 계정 추가

`sudo adduser guest2`
___
23) uname
-  -a 옵션 디테일 정보 
- 시스템 정보를 확인!

24) hostname
- Jaydens-MacBook-Pro.local

25) reboot
- 재부팅
`sudo reboot`

26) halt 
- 시스템 완전히 셧다운 **주의! -p옵션 파워까지 날림!
`sudo halt -p` 

























