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
```

```



















