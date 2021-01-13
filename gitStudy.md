
# 원격 저장소 깃허브에 실수로 올린 파일 또는 폴더 삭제 하기

## 원격 저장소와 로컬 저장소에 있는 파일을 삭제한다.
- `git rm file_name`

## 원격 저장소에 있는 파일 또는 폴더 삭제
- `git rm --cached 파일명`
- `git rm --cached -r 폴더명`

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


