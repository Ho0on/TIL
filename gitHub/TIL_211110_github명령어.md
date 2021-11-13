# Github 명령어

### 1. Git으로 프로젝트 관리 시작 : `git init`
- 프로젝트를 진행 할 폴더를 하나 생성한다.
- 터미널에서 프로젝트 폴더로 이동한 이후에 아래의 명령어로 `git` 관리를 시작한다.
```
$ git init
```

### 2. Commit을 위한 Staging : `git add`
- 현재 코드 상태의 스냅샷을 찍기 위한 파일 선택 (Staging Area에 파일 추가)
- . 을 통해 모든 변경 사항을 staging area로 추가한다.
```
$ git add [파일 이름]
$ git add . 
```


### 3. 버전 관리를 위한 스냅샷 저장 : `git commit`
- 현재 상태에 대한 스냅샷을 `commit`하여, 버전 관리를 진행한다
```
$ git commit -m "커밋 메시지"
```

### 4. 원격 저장소 정보 추가 : `git remote`
- Github 원격(remote) 저장소(repository)를 생성하고 프로젝트 폴더와 연결한다.
```
$ git remote add origin [github 원격 저장소 주소]
```

### 5. 원격 저장소에 저장 `git push`
- 최종적으로 Github 원격 저장소에 push한다.
```
$ git push origin master
```

### 6. 그 외 명령어
- 현재 `git` 의 상태를 조회 `git status`
```
$ git status
```
- 버전 관리 이력을 조회
```
$ git log
```

