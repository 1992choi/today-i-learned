# Git
- Inflearn > 모두의 깃 & 깃허브



<br><br>



## 개념 정리
### Git이란?
- 깃(Git)은 소프트웨어 개발에서 사용되는 분산 버전 관리 시스템이다.
- 즉, 여러 명이 하나의 프로젝트를 개발할 때, 소스코드의 변경 내역을 추적하고 관리하여 버전을 관리할 수 있는 도구이다.

<br>

### Git 저장소 구조
![image](https://github.com/1992choi/git/assets/27760576/69e54cd4-b495-4b69-b3c8-861fc0d5d9fa)
- 작업 공간(Working Directory)
  - 사용자가 실제로 작업하는 공간.
  - PC에서 프로젝트를 진행하는 폴더이다.
- Staging 영역
  - 로컬 저장소에 저장하기 전 저장하는 공간.
  - 여기에서 프로젝트의 버전을 만든다.
- Local Repository
  - 변경 내역들과 함께 파일이 저장되는 공간.
  - 프로젝트의 변경 사항들이 기록된다.
- Remote Repository
  - 온라인상의 원격 저장소.
  - Github가 해당된다.

<br>

### Git 되돌리기
- Git에서는 작업 내용에 대한 커밋을 아예 취소(Reset)하거나 되돌리기(Revert) 할 수 있다.
- Reset
  - 시계를 마치 과거로 돌리는 듯한 행위
  - 특정 커밋으로 돌아가는 행위이다.
  - 특정 커밋 이후의 커밋이력은 모두 없어지게 된다.
  - Reset에는 3가지 옵션이 있다.
    - soft : 커밋 취소. 스테이징 상태로 유지
    - mixed : 커밋 취소 및 스테이징 취소. 내 로컬 변경 상태로 유지.
    - hard : 커밋 취소 및 스테이징 취소 및 로컬 변경 상태 취소.
- Revert
  - 특정 사건을 없었던 일로 만드는 행위
  - 특정 커밋으로 돌아가기 위해 새 커밋을 수행한다.
- 주의사항
  - reset은 커밋을 완전 삭제하면서 과거 커밋으로 돌아가는 것이기 때문에 원격저장소 및 팀원들이 작업하는 타 브랜치와 추후에 충돌을 일으킬 수 있다.
  - 때문에 협업 프로젝트의 경우에는 git revert를 써서 이전 커밋으로 돌아가는 방법이 안전하다.

<br>

### Git 임시저장
- Git에서는 stash 명령어를 사용하여 현재 작업내용을 임시로 저장할 수 있다.
- 다른 브랜치로 checkout을 해야 하는데, 아직 현재 브랜치에서 작업이 끝나지 않았다면 커밋을 하기가 애매하다.
  이런 경우 stash를 이용하면 작업중이던 파일을 임시로 저장해두고, 현재 브랜치의 상태를 마지막 커밋 상태로 초기화 할 수 있다.
  그 후에 다른 브랜치로 이동하고 작업을 끝낸 후에 작업 중이던 브랜치로 복귀한 후, 이전에 작업하던 내용을 복원할 수 있다.

<br>

### 브랜치(Branch)
- 브랜치란?
  - ![image](https://github.com/1992choi/git/assets/27760576/1e4990ae-4116-4d2d-af22-2fd7e7e7b891)
  - 브랜치는 사용자가 독립적으로 작업을 진행할 수 있도록 돕는 작업 흐름이다.
  - 깃에서 브랜치는 여러 작업을 각각 독립된 공간에서 진행할 수 있도록 하는 기능이다.
  - 하나의 브랜치는 독립된 워크스페이스, 인덱스, 로컬 레포지토리, 리모트 레포지토리 공간을 가진다.
  - 이처럼 브랜치를 이용하면 하나의 프로젝트에서 여러 사람이 동시에 본인의 작업을 진행할 수 있다.
- 브랜치를 이용한 작업 흐름
  - 각 개발자는 메인 브랜치에서 각자 자신이 작업할 새로운 브랜치를 만든다.
  - 각 개발자는 본인이 만든 브랜치 위에서 작업한다.
  - 작업 완료 후 리모트 레포지토리의 자신이 작업한 브랜치를 푸시한다.
  - 리모트 레포지토리에서 메인 브랜치로 풀 리퀘스트(PR, Pull Request)를 진행한다.
  - 협업하는 다른 개발자에게 리뷰를 받는다.
  - 리뷰 및 합의 후 메인 브랜치에 머지한다. 

<br>

### 병합(Merge)
- 병합(Merge)이란?
  - 병합(Merge)은 Git에서 두 개의 branch를 하나로 통합하는 과정이다.
  - 병합에는 Fast-Forward Merge 방식과 3-way Merge 방식이 있다.
- Fast-Forward 방식
  - ![image](https://github.com/1992choi/git/assets/27760576/d1491b31-3844-4790-8329-927fcb40ff9c)
  - 서로 다른 브랜치의 base 커밋에 내용이 변경되지 않았을 때 사용된다.   
    Ex) 기존 Main 브랜치에서 새로운 브랜치인 Feature를 생성 한 후, Main에서는 더 이상의 커밋이 없고 Feature에서만 커밋이 발생한 경우.
  - Merge에 의해서 새로운 커밋이 만들어지지않고, HEAD의 위치만 이동된다.
- 3-way 방식
  - ![image](https://github.com/1992choi/git/assets/27760576/a38d7358-d7eb-40cc-86d5-dab572659966)
  - 각 브랜치에서 새 커밋이 발생했을 때 사용된다.
  - 두 브랜치의 코드를 합쳐서 새로운 커밋을 자동 생성해준다.

<br>

### 재배치(Rebase)
- 재배치(Rebase)란?
  - base를 재설정한다는 의미이다.
  - 하나의 브랜치가 다른 브랜치에서 파생되서 나온 경우, 다른 브랜치에서 진행된 커밋을 다시 가져와서 base를 재설정하는 것을 의미힌다.
- 장점
  - Rebase를 하면 파생된 브랜치의 커밋이력이 기준 브랜치와 같아지므로 작업순서대로 커밋 이력이 남게된다. 때문에 커밋 히스토리가 시간 순서대로 반영되어 이력관리가 용이해진다.
  - 나아가 merge를 통해 발생하는 불필요한 병합 커밋을 제거할 수 있다.
- Merge와의 차이점
  - Merge
    - ![image](https://github.com/1992choi/git/assets/27760576/e403b5b7-2bfc-439c-94aa-0251354580e8)

  - Rebase
    - ![image](https://github.com/1992choi/git/assets/27760576/d28b1253-fef5-442f-baae-f4072ffc43d9)

<br>
 
### 원격 저장소와의 상호작용
- 원격저장소(Github)와의 4가지 상호작용 방법은 아래와 같다.
  - 클론(clone)
    - 원격 저장소의 파일을 로컬 저장소로 복제한다.
  - 푸시(push)
    - 로컬 저장소의 파일을 원격 저장소에 반영한다.
  - 패치(fetch)
    - 원격 저장소의 변경사항을 가져오되 병합하지는 않는다.
  - 풀(pull)
    - 원격 저장소의 변경사항을 가져온 후 병합한다.

<br>
 
### Pull Request
- Pull Request란?
  - 다른 사용자가 작성한 저장소에서 변경 사항을 병합(merge)하기 위한 요청을 의미한다.
- Pull Request 순서
  1. Fork
     - 타겟 프로젝트의 Repository를 자신의 Repository로 Fork한다.
  2. Clone
     - 자신의 로컬에 Fork한 Repository를 Clone한다.
  3. Branch 생성
     - 작업을 위해 Branch를 생성한다.
  4. 수정, add, commit, push
     - 코드를 수정한 후 add > commit > push 한다. 
  5. Pull Request 생성
     - push 후 깃허브의 해당 레파지토리에서 'Compare & pull request' 버튼을 클릭한다.
     - 수정에 대한 코멘트를 작성하고 'Create pull request' 버튼을 클릭한다.
  6. Merge Pull Request
     - 원본 Repository의 개발자가 승인하면 해당 프로젝트에 수정사항이 Merge된다. 
  7. Branch 삭제
     - 승인이 완료되어 Merge가 되었다면, 더 이상 사용하지 않게될 Branch를 삭제한다.



<br><br>



## 명령어
### 저장소와 버전 만들기
- git init
  - 새로운 로컬 저장소 생성
  - 명령어가 입력되면 .git 디렉토리가 생성된다.
- git status
  - Git 저장소의 상태를 출력하는 명령어
- git add [파일명]
  - Staging area에 파일을 저장한다.
  - Ex) git add a.txt
- git add .
  - 현재 디렉토리의 모든 변경 내용을 Staging area에 저장한다.
- git commit
  - Staging area에 저장되어있는 변경 사항들을 로컬저장소에 등록한다.
  - 커밋 메시지의 제목과 내용을 입력하고 싶은 경우
    - git commit을 입력하면 vi편집기가 활성화 된다.
  - 커밋 메시지의 제목만 입력하고 싶은 경우
    - git commit -m "커밋 제목"

<br>

### 커밋 이력 조회
- git log
  - 커밋 이력 상세 조회
- git log --oneline
  - 커밋 이력 중 커밋 ID와 타이틀 메시지만 조회
- git log -p / git log --patch
  - 수정 내역(=diff)을 조회
- git log --graph
  - 브랜치와 머지 히스토리 정보까지 아스키 그래프로 보여준다.
- git log --since=[기간]
  - 특정 기간 내의 log만 조회한다.
  - Ex)
    - git log --since=1.weeks
    - git log --since=1.hour
- git log --branches
  - 다른 브랜치의 커밋 이력까지 조회한다.

<br>

### 태그 관리
- git tag [태그명]
  - 최근 커밋에 태그를 추가한다.
  - Ex) git tag v0.0.1
- git tag [태그명] [커밋ID]
  - 특정 커밋에 태그를 추가한다.
  - Ex) git tag v0.0.1 fdc30cc
- git tag / git tag --list / git tag -l
  - 태그 목록을 조회한다.
- git tag --delete [태그명] / git tag -d [태그명]
  - 태그를 삭제한다.
  - Ex) git tag --delete v0.0.1

<br>

### 작업내용 비교
- git diff
  - 커밋된 파일과 Working Directory에서 수정 중인 파일상태를 비교한다.
- git diff --staged
  - 커밋된 파일과 Staging Area의 파일상태를 비교한다.
- git diff [변경전 커밋ID] [변경후 커밋ID]
  - 커밋 간의 파일상태를 비교한다.
  - [변경전 커밋ID]가 반드시 [변경후 커밋ID]보다 이전 커밋이어야한다.

<br>

### 작업 되돌리기
- git revert [취소할 커밋ID]
  - 작업한 내용을 Revert한다.
  - Ex) git revert ccccccc
    - 'ccccccc'의 변경사항을 취소 시킨다.
    - 커밋순서가 aaaaaaa -> bbbbbbb -> ccccccc -> ddddddd 이라고 가정할 때, git reset ccccccc를 입력하면 bbbbbbb에서 작업한 내용까지가 보존된다.
- git reset --[옵션] [되돌아갈 커밋ID]
  - 작업한 내용을 Reset 시킨다.
  - Default 옵션은 mixed이다.
    - soft : git reset --soft [되돌아갈 커밋ID]
    - mixed : git reset [되돌아갈 커밋ID] / git reset --mixed [되돌아갈 커밋ID]
    - hard : git reset --hard [되돌아갈 커밋ID]
  - Ex) git reset ccccccc
    - 커밋순서가 aaaaaaa -> bbbbbbb -> ccccccc -> ddddddd 이라고 가정할 때, git reset ccccccc를 입력하면 ccccccc에서 작업한 내용까지가 보존된다.

<br>

### 작업 임시저장
- git stash
  - 마무리하지 않은 작업을 스택에 잠시 저장한다.
  - 이를 통해 아직 완료하지 않은 일을 commit하지 않고 나중에 다시 꺼내와 마무리할 수 있다.
  - -m옵션을 사용하여 간단한 코멘트를 작성할 수 있다.
    - Ex) git stash -m "add subtitle on a.txt"
- git stash list
  - 임시저장한 목록을 조회한다.
- git stash apply [stash 이름]
  - 임시저장한 내용을 다시 가져온다.
  - Ex) git stash apply stash@{0}
- git stash drop [stash 이름]
  - 임시저장한 내용을 삭제한다.
  - Ex) git stash drop stash@{0}

<br>

### 브랜치 관리
- git branch [생성할 브랜치 이름]
  - 브랜치를 생성한다.
  - Ex) git branch foo
- git branch
  - 브랜치를 조회한다.
- git checkout [브랜치 이름]
  - 특정 브랜치로 이동한다.
  - Ex) git checkout foo
- git checkout -b [브랜치 이름]
  - 특정 브랜치를 생성한 후 해당 브랜치로 이동한다.
- git merge [병합하고자 하는 브랜치 이름]
  - 특정 브랜치의 작업사항을 병합한다.
  - Ex) git merge foo
    - 현재 작업 디렉토리가 master인 경우, foo의 작업 내용을 master로 병합한다.
- git branch -d [삭제할 브랜치 이름]
  - 브랜치를 삭제한다.
  - Ex) git branch -d foo

### Rebase
- git rebase [기준이 될 브랜치 이름]
  - 브랜치를 재설정한다.
  - Ex) git rebase master
    - 현재 체크아웃된 브랜치가 foo라고 가정할 때, 위의 명령어를 실행한다면 현재 master 브랜치에서 작업된 내용을 기반으로 재설정 된다.























