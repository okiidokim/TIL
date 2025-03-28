# ✏️ 깃/깃허브 정의

### Git

- 정의 : 파일의 변경 사항을 함께 관리하고 조율하기 위한 분산 버전 관리 시스템
- 분산 : 흩뿌려짐
- 버전 : 기록/히스토리 번호
↔ 중앙 집중식 관리 시스템 : google docs 

### Github

- 정의 : 깃을 사용하는 웹 서비스
- bitbucket이라는 서비스도 존재

--- 

# ✏️ 깃허브 관련 명령어
- git init
    - 워킹 디렉토리 생성하는 명령
- git add
    - untracked file에서 stage로 올리는 명령
    - git add . / git add * 지양 → 전체를 추가하는 명령이기 때문
- git commit
    - 저장/기록의 의미
    - git commit -m "메시지 제목"
    - -m이 없으면 제목 + 내용으로 커밋 가능
    - stage에서 history로 올리는 명령
- git push
    - git push <원격 저장소명> <브랜치명>
    - 원격 저장소명의 해당 브랜치에 올리겠다. <br>
    💡 예전에 블로그 보면서 master가 기본 브랜치다, main이 기본 브랜치다 말이 많아서 뭐가 맞지 했는데 19년도 이후부터 master라는 단어 의미 때문에 바뀌었다는 사실이 꽤 흥미롭 그냥 main이 내가 할 땐 기본 브랜치여서 사람마다 다른가 난 뭐 main이 기본인 걸로 알고 넘어 가야지 했었음.
- git clone "원격 저장소 주소"
    - 처음 원격 저장소에서 로컬로 파일들을 받아올 때 사용하는 명령어
- git pull
    - git fetch + git merge
    - 두 명령어를 따로 사용하는 것이 더 일반적
    - 코드 충돌을 방지하기 위해 pull을 먼저 하고 push하는 것을 권장
- git stash
    - unstaged file을 비우고 임시 저장 공간으로 보내는 명령어
- git remote
    - git remote add <원격 저장소명> <원격 저장소 주소>
    - 원격 저장소 명을 원격 저장소의 주소의 별명처럼 사용하고 관리하기 위한 명령어
- git restore
    - 복구하다
    - 가장 마지막 커밋 이후로 수정된 코드를 다시 마지막 커밋 상태의 코드로 돌려놓는 것
    - a → b → c → d까지 진행 후 → e로의 커밋은 올리지 않았지만 d와 다른 상태일 때 d로 돌아가고자 함
- git revert
    - 되돌리다 
    - a → b → c → d의 기록이 있고 d → a로 돌아가고 싶을 때 기록을 남기며 돌아감
    - 협업 시 d → a의 기록이 남아있어야 다른 개발자가 알고 작업할 수 있음
- git reset
    - revert와 유사하지만 기록이 남지 않는다는 점에서 가장 큰 차이가 있음
    - 앞으로 사용할 일 없음
- git diff
    - 가장 마지막 커밋 이후로 변경 사항을 보여주는 명령
- git difftool
    - git diff 명령의 시각화 버전
    - 변경 사항의 GUI로 보여줌
- git log
    - 깃 커밋 히스토리를 보는 명령
    - git Lens 확장 프로그램으로 vsc에서 쉽게 볼 수 있음
- git branch
    - 새로운 브랜치 생성
    - git branch [새 브랜치명]
- git checkout
    - 원하는 브랜치로 변경
    - checkout 뒤에 이동 완료 상태로 원하는 브랜치를 작성
    - git checkout [원하는 브랜치명]

- git status
    - tracked, untracked, stage 중 어느 상태인지 알려주는 명령

- 추가 명령어
    - git show
    - git blame

--- 

# ✏️ 깃허브 머지 방법
### 3-way
- 흔히 사용하는 병합 방법
- main, 파생된 다른 브랜치가 있을 때 모든 기록을 남긴 채로 main에 합치는 방법
1. 파생이 시작된 시점
2. main 브랜치의 마지막 커밋 시점
3. 파생된 브랜치의 마지막 커밋 시점

### fast-forward
- 새 브랜치의 파생 이후 main에는 커밋이 없는 상태
- 파생된 새 브랜치를 main 브랜치로 변경하면서 커밋하고 싶을 때 사용

### rebase-merge
- 파생된 브랜치의 커밋 기록까지 모두 main으로 병합하고 싶을 때
- 두 브랜치의 충돌 없음이 보장돼야 함
- 또는 충돌 파일을 개발자가 하나하나 보면서 병합할 것

--- 

# ✏️ 깃허브 활용

### .gitignore
- 젯브레인을 사용할 때 자체 폴더를 만드는데 vsc에서 작업하는 사람들에게는 필요 없으니 추가 → 인터넷 복붙
    - 이미지, 보안 정보 등
- 유저가 업로드한 이미지는 깃허브에 올라가지 않아야 함
- 서버에 저장이 필요한 아이디, 비밀번호와 같은 보안 정보는 깃허브에 올라가지 않아야 함
- 프론트엔드에서 리액트 작업할 때 카카오나 구글 api 쓰면 .env 파일에 변수명이랑 api 키 정의하고 .gitignore에 .env를 추가하곤 했음

### git flow 브랜치 관리 전략
- feature/기능명
- 개발자명/기능명<br>
    💡난 이걸 많이 사용해왔음 ㅎㅎ 귀찮을 땐 이름만 대충해서 브랜치 팔 때도 종종 있었다~

### github 이슈 관리 전략 
- jira-001
    - 회사에서 지라를 사용할 때 디자인/기획부에서 각 기능으로 생각하거나 태스크의 고유 티켓 번호가 있을텐데 해당 부분을 해결할 때 커밋 메시지의 제목, 이슈의 제목으로 많이 사용
- closed #1
    - 지라를 사용하지 않거나 지라를 사용하더라도 문제 해결의 경우 이처럼 처리하는 경우도 있음
    - 이슈 생성 시 #1과 같이 고유 번호가 있을 것 (이슈를 열었기 때문에 open)
    - 문제 해결 시 closed로 함
- 이슈 템플릿
    - 개인 조직 설정에서 세팅 가능<br>
    💡 협업에서 굉장히 중요하다고 들은 적은 많은데 실제로 사용해본 적이 없어서 제대로 깃허브를 사용해야 실질적인 의미가 있겠다 싶은..~~

### 코드 병합 방법
- fork
    - 조직의 레포를 개인 레포로 fork 해온 후 작업하는 방식
    - 일반적으로 contributor로서 작업하는 경우가 많음
    - 이 경우 조직의 레포는 upstream, 개인의 레포는 origin
-  바로 pr
    - 일반적으로 회사 내부 사람의 경우, 별도의 권한을 이미 가지고 있기에 fork가 필요 없음
    - 이 경우 조직의 레포는 origin으로 사용 가능

--- 

# 👀 느낀점
학교 다니고 플젝하면서 깃허브 쓴 건 ㄹㅇ 헛으로 썼다는 느낌을 많이 받았다. 그래도 덕분에 깃허브 프로필에 대충 리드미도 올려봤다. 아직 다 안 해서 나중에 좀더 수정할 예정임.

그리고 깃 렌즈도 설치했는데 이것도 앞으로 협업하면서 써봐야겠다.

지금까지 잘못 써왔던 부분도 보이고 사실 깃데탑을 항상 써왔던 터라 저 명령어들의 의미를 거의 모르고 있었다.

그런 나에게 깃데탑 쓰면서도 충돌 생길 때 GPT에 물어보는 게 다였는데 깃허브 관련 개념 정리하면서 아주 유익한 시간이었음

근데 pull 먼저 하고 push하는 건 아직 이해가 잘 안돼서 직접 해봐야 할 듯 하다. 왜냐하면 지금까지 작업 전에 pull하는 건 당연했는데 작업 후 push 전에 pull 하는 건 로컬에서 충돌나는 게 겁나서 매번 그냥 push 했었는데 깃허브에서 충돌 다루는 것보다 로컬에서 충돌 다루는 게 더 협업에 맞는 방식인지 몰랐다.

그리고 플젝할 땐 겁나서 우선 깃데탑 쓸 듯? ㅎㅎ

기록의 중요성도 중요성인데 어디에 어떻게 작성해서 스스로를 얼마나 잘 홍보할 수 있는지도 중요하다는 생각이 드는 강의였다.
