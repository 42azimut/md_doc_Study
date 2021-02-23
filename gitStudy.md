## ![그림이름](링크)

![git Command Overview]()<https://github.com/42azimut/md_doc_Study/blob/main/IMG_5903.JPG">

# 원격 저장소 깃허브에 실수로 올린 파일 또는 폴더 삭제 하기

## 원격 저장소와 로컬 저장소에 있는 파일을 삭제한다.
- `git rm file_name`

## 원격 저장소에 있는 파일 또는 폴더 삭제
- `git rm --cached 파일명`
- `git rm --cached -r 폴더명`

## .gitignore 작성 예시
```
#확장자가 .class인 파일은 무시합니다.
*.class

#.class 파일들은 모두 무시되지만, HelloWorld.class만큼은 무시하지 않습니다.
!HelloWorld.class

#현재 디렉터리에 있는 /Test.java 파일은 무시되지만,
#subDir/Test.java 같이 특정 디렉터리 하위에 있는 Test.java는 무시되지 않습니다.
/Test.java

#target/ 디렉터리에 있는 모든 파일 무시합니다.
target/

#src/ 하위의 .java 파일은 무시되지만 /src/main/ 하위의 .java 파일은 무시되지 않습니다.
src/*.java

#src/ 하위에 존재하는 모든 디렉터리의 .txt 파일을 무시합니다.
src/**/*.txt

출처: https://dololak.tistory.com/306 [코끼리를 냉장고에 넣는 방법]
```

### 위에 작업 하고 나서 
- `git commit`
- `git push`  
### 해주면 된다.
___

### - origin == github의 현재 리포지터리의 alias 관행적으로 origin 이라 함! 주소 쓰기 귀찮음!

## git 생성(git hub 리포지터리 생성해둠)
- `git init`
- `git add "file"`
- `git commit -m "message"`
- `git branch -M main`
- `git remote add origin github.adress` 
- `git push -u origin main`

##
- `git pull origin main`

## branch
- `git branch branch_name`
- `git checkout branch_name`




