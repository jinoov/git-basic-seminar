---
theme: seriph
themeConfig:
  primary: '#47be9b'
  fontWeight: 500
class: text-center
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: Git Basic Seminar
fonts:
  sans: 'Noto Sans KR'
  local: 'Noto Sans KR'
---

# Git/GitHub 101

---

# 발표자 소개

- 산업공학과 재학 중
- 웹개발을 좋아합니다.
- 생산성을 높이는 방법들(~~날먹~~)에 관심이 많습니다.

---

# Table Of Contents

1. Git이란? 대체 왜 쓰는가?
2. 실습환경 구축하기
3. 개념1) Local and Remote
4. 개념2) 작업공간 분리와 협업하기
5. 오픈소스에 기여하기
6. Git의 내부원리
7. 개념3) 기록조작하기
8. GitHub 메뉴 소개
9. 외부도구와의 연동

---

# 1. Git이란? 대체 왜 쓰는가?

---

# Git이란?

<ul>
    <li style="color: gray; opacity: 0.3">학교에서 알려주지 않지만 학생들이 당연히 알고 있을것이라 가정되는 툴</li>
    <li>리눅스 토발즈라는 매우 똑똑한 프로그래머가 만든 <b>분산형 버전 관리 시스템</b></li>
    <li><code>분산 == 협업</code></li>
    <li><code>버전 == 기록</code></li>
    <li style="color: red; font-weight: 700">협업을 용이하게 하는 프로그램 기록 관리 시스템</li>
</ul>

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/git-logo.png" width="150" alt="">
    <p style="color: #666; font-size: 14px">Global Information Tracker(?)</p>
</div>

---

# Git을 대체 왜 쓰는가?(문제의식)

- 조별과제 PPT를 만들 때를 상상해보자.
- 아래 방식의 문제는 무엇일까?

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/team-ppt.png" width="300" alt=""/>
</div>

---

# 조별과제의 어려움

<ol>
    <li>Timeline과 변동사항을 알기 힘들다.</li>
    <li>여러 사람이 함께 협업한다면, 결국 <b style="color: red">수동으로</b> 병합하는 과정이 필요하다.</li>
    <li>???: 런어스에 제출하셨나요?</li>
</ol>

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/team-ppt.png" width="300" alt=""/>
</div>

---

# 구글 슬라이드

<ul>
    <li>대안이 될 수 있는 도구: Google Slide</li>
    <li>변동사항의 파악이 용이</li>
    <li>변경사항이 자동으로 병합됨</li>
</ul>

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/google-slide.png" width="500" alt=""/>
</div>

---

# 구글 슬라이드의 한계

<div>
    <h4 style="color: red; font-weight: 700">그러나...</h4>
    <ul>
        <li>누구 한명이 실험적인 시도를 하고 싶다면?</li>
        <li>실시간 변경은 늘 옳을까?</li>
        <li>???: 아니 이거 누가 수정한거지</li>
    </ul>
</div>

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/google-slide.png" width="500" alt=""/>
</div>

---

# 2. 실습환경 구축하기

---

# Git Download

- Git은 하나의 프로그램. 설치가 필요하다.

<div style="display: flex; align-items: center; gap: 20px; margin-top: 40px">
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/git-download.png" width="500" alt=""/>
    </div>
</div>

---

# Git 외부 접근 도구들

- Git을 외부에서 접근하는 도구가 필요
- 더 세밀하게 조작하고자 하거나, 외부 서버에 붙어서 작업하고 싶다면 CLI
- 일반적인 작업 + 개념이해에는 GUI로도 충분
- CLI, GUI 둘다 있는 vscode를 통해 실습 진행 예정

<div style="display: flex; align-items: center; gap: 20px">
    <div>
        <p>CLI: Command Line Interface</p>
        <img src="/images/cli.png" width="300" alt=""/>
    </div>
    <div>
        <p>GUI: Graphic User Interface</p>
        <img src="/images/gui.png" width="300" alt=""/>
    </div>
</div>

---

# GitHub는 그러면 뭐에요?

- 버전 관리되고 있는 프로그램을 업로드하는 저장소
- 제일 대중적인 저장소가 GitHub

<div style="display: flex; align-items: center; gap: 20px; margin: 30px 0">
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/github.png" width="100" alt=""/>
    </div>
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/gitlab.png" width="100" alt=""/>
    </div>
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/gitbucket.png" width="100" alt=""/>
    </div>
</div>

- 일반적인 상황은 아니지만 원격 저장소를 여러 개 둘 수도 있다.
- `가장 근본이 되는 저장소 == origin`

---

# 딴소리) MS가 주도하는(?) 개발 생태계

- 합이 잘 맞아서 같이 쓰면 좋다.

<div style="display: flex; align-items: center; gap: 20px; margin: 30px 0">
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/ms-ecosystem.png" width="400" alt=""/>
    </div>
</div>

---

# 실습 환경만들기

1. 로컬환경에서 빈 프로젝트(폴더) 만들기
2. `git init` 명령어로 '나는 깃을 사용할거야' 선언하기
3. GitHub 로그인하고 Repository(업로드 하는 공간) 생성하기
4. `git remote add origin <저장소 주소>` -> 연결해주기

<div style="display: flex; align-items: center; gap: 20px; margin: 30px 0">
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/git-repository-start.png" width="500" alt=""/>
    </div>
</div>

---

# 3. 개념1) Local and Remote

---

# Local and Remote

- Remote: 다른 사람들과 공유되는 공간. 지금까지의 작업사항이 병합되어 있음.
- Local: 나만의 공간. 실험적인 시도들을 할 수 있다.

<div style="margin-top: 20px">
    <img src="/images/local-and-remote.png" width="300" alt=""/>
</div>

---

# Local에서의 Flow

1. 파일들을 생성한다.
2. 업로드하고 싶은 것들만 상자에 담는다. (`add`)
3. 상자에 송장을 붙인다. (`commit`)
4. 서버로 보낸다. (`push`)

---

# Layers in Local

<div>
    <ul>
        <li>History: 포장을 마친 상자들</li>
        <li>Staged: 상자 안의 영역</li>
        <li>Unstaged: 상자 밖의 영역</li>
        <li>Untracked: 아예 관심을 갖지 않는 영역</li>
    </ul>
    <hr style="margin: 20px 0"/>
    <p>Q. 굳이 이렇게까지 복잡하게 해야하는가?</p>
</div>

---

# Remote의 변경사항 내려받기

- 밀었으니(`push`) 당겨온다(`pull`)
- Question. 내려받은 내용이 작업내용을 덮어씌운다면..?

---

# Remote의 변경사항 내려받기

- Answer. Git은 애매한 상황에서는 사용자에게 권한을 위임한다

```md
# 해결 방법

1. editor열고 conflict 해결하기
   - `Accept Current Change`: 내 작업내용을 선택
   - `Accept Incoming Change`: pull된 작업내용을 선택
   - `Accept Both Changes`: 둘다 선택
2. add & commit
```

---

# Remote의 변경사항 내려받기

- token 입력이 필요한 경우(Windows, git 처음 설치, ...)
  1. Settings > Developer Settings > Personal access tokens에서 토큰을 발급받기
  2. `git config --global credential.helper store`: 최초 한번만 token 입력가능하게

---

# Remote의 변경사항 내려받기

- 충돌이 덜 나게하려면?

<div style="margin: 40px 0">
    <img src="/images/woowahan-comment.png" width="600" alt=""/>
    <p style="font-size: 12px; color: #6e6e6e">Reference: 우아한기술블로그 - 우린 Git-flow를 사용하고 있어요</p>
</div>

- 그래도 충돌은 난다. 충돌발생시 독단적으로 행동하지 말고 꼭 동료와 소통하자

---

# 명령어 요약

- `git status`: staging area / unstaging area 확인
- `git add <원하는 파일>`: 변경 사항들을 상자 안에 넣는다(모든 파일을 다 상자에 넣고 싶으면 `git add .`)
- `git commit -m '<메시지>'`: 상자에 송장을 붙인다(당연히 상자에 든게 없으면 송장도 못붙임!)
- `git push`: 송장붙인 상자를 서버에 보낸다
- `git pull`: 서버에서 변경사항을 내려받는다(뒤에서 다른 의미로도 쓰인다)
- `git clone <원하는 remote 주소>`: 맨 처음 시작할 때
- `git log`: 히스토리 보기
- `git diff`: 현재시점의 변경사항 보기

CLI Tips

- `<명령어> --help`: 웬만한 옵션들 다 나옴
- `<명령어> --인자이름=인자`: 함수에 인자 넘기듯이 스크립트에 인자 넘기기

---

# 4. 개념2) 작업공간 분리와 협업하기

---

# 문제

- 만약 두 사람이 하나의 remote를 바라보고 있다면?

<div style="display: flex; align-items: center; margin: 20px 0">
    <img src="/images/one-remote-two-locals.png" width="300" alt=""/>
</div>

- B가 remote에 push하는걸 A 입장에서 리뷰할 수 없다
- B의 코드에 문제가 있었다면 큰 문제를 가져올 수 있음

---

# 작업공간 분리하기

- 작업공간을 분리함으로써 독립성을 확보하기
<div style="display: flex; align-items: center; margin-top: 20px">
    <img src="/images/separate-workspace.png" width="400" alt=""/>
</div>

---

# Pull Request(PR)

- 하나의 remote에서 다른 remote로 작업물을 업로드하고 싶은 경우
- `Git`의 기능이 아닌 `GitHub`의 기능임을 인지하자!

<div style="display: flex; align-items: center; margin-top: 20px">
    <img src="/images/pull-request.png" alt=""/>
</div>

---

# Pull Request

- Reviewer와 label 등을 지정해주면 프로젝트 관리에 도움이 된다
- 코드 리뷰 등을 충분히 거친 이후 remote에 병합

<div style="display: flex; align-items: center; margin-top: 20px">
    <img src="/images/code-review.png" width="330" alt=""/>
</div>

---

# Issue

- 무작정 PR을 날리기보다는 Issue를 생성하고 해당 Issue를 commit이나 PR에 연동해보자
- `#<Issue Number>`를 commit이나 PR에 넣으면 히스토리 파악이 보다 용이해진다

<div style="display: flex; align-items: center; margin-top: 20px">
    <img src="/images/big-issue.png" width="200" alt=""/>
</div>

---

# Fork

- 조금 더 과감하게 실험을 하고 싶다면??

<div style="display: flex; align-items: center; margin-top: 20px">
    <img src="/images/github-fork.png" width="600" alt=""/>
</div>

---

# Clone vs. Fork

- `clone`
  - 넓은 의미의 repository로 보았을 때, repository를 새로 생성하는 명령어가 아니다.
  - 좁은 의미의 local repositroy만을 생성하는 명령어이다.
- `fork`
  - 넓은 의미의 repository를 생성하는 기술이다.

<div style="display: flex; align-items: center; margin-top: 20px">
    <img src="/images/clone-vs-fork.png" width="400" alt=""/>
</div>

---

# 명령어 요약

- `git branch`: 브랜치 리스트 보기
- `git branch -c <브랜치명>`: 브랜치만들기
- `git branch -d <브랜치명>`: 브랜치없애기
- `git switch(checkout) <브랜치명>`: 브랜치 변경하기

**중요**

- Pull Request, Fork 등은 `Git`이 아닌 `Github`의 기능
- remote-local이 아닌 remote-remote는 CLI(git)로 처리하는게 아니다

---

# Tree는 재귀적이다

- 사람이 많다면 더 잘게 쪼갤 수도 있다(Git Flow)
- 그렇지만 잘게 쪼개는게 꼭 정답은 아닐수도?(Trunk Based Development)

<div style="display: flex; align-items: center; gap: 30px; margin-top: 40px">
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/git-flow.png" width="400" alt=""/>
    </div>
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/trunk-based-development.png" width="400" alt=""/>
    </div>
</div>

---

# 5. 오픈소스에 기여하기

---

# 오픈소스에 기여하기

- 오픈소스는 많은 사람들이 함께 사용하는 소스이기 때문에, 브랜치를 파기보다는 fork를 통해 작업공간을 분리하기를 일반적으로 권장
- fork -> Pull Request를 통해 오픈소스에 기여해보자
- https://github.com/jinoov-sandbox/some-opensource

---

# 오픈소스와 나와의 방향성이 다르다면?

1. 포크뜬 녀석을 사용하기
2. maintainer가 병합해줄때까지 참고 기다리기
3. 최대한 건드리지 않는 선에서 다른 코드를 조작하기

---

# 1주차 Remind 🚀

---

# Git의 사용 목적

- 버전 관리(언제, 누가, 어떻게, 왜 수정했는가에 대한 파악)
- 자동 병합

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/real-last.jpeg" width="300" alt="">
</div>

---

# GitHub의 사용 목적

- Local에서 관리되는 Git의 내용을 remote에 백업해두기
- Remote의 세계로 진입한 이후, 보다 많은 기능들에 대한 접근이 가능하다.
  - fork, pull request, ...

---

# Git & GitHub Architecture

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/github-architecture.png" width="1000" alt="">
</div>

---

# Repository 새로 생성하기(only in CLI)

1. 프로젝트 생성하기
2. 깃을 사용한다고 선언하기
   - `git init`
3. 깃허브 저장소 만들기
   - `git remote add origin <주소>`
4. 상자만들기, 송장붙이기
   - `git add .`
   - `git commit -m '<메시지>'`
5. 만든 상자를 서버에 보내기
   - `git push`

---

# Repository 새로 생성하기(only in VSCode)

1. 프로젝트 생성하기
2. 깃을 사용한다고 선언하기
   - `Initialize Git Repository` 클릭
3. 상자만들기, 송장붙이기
   - (+) 버튼 & `Commit` 클릭
4. 깃허브 저장소 만들기
   - `Publish Branch` 클릭
   - Public: 링크만 있으면 누구나 접속 가능. / Private: 초대를 받아야만 접속 가능
5. 만든 상자를 서버에 전송하기
   - `Sync Changes` 클릭

---

# 이미 존재하는 Repository에 붙어서 작업하기

1. 프로젝트 clone받기
   - 접근 권한이 있다는 전제하에!
2. 상자만들고 송장붙이고 푸쉬하고 반복
3. 브랜치를 새로 만들 수도 있다
   - `git branch -c <브랜치명>`: 브랜치 만들기
   - `git switch <브랜치명>`: 브랜치 전환하기
4. 브랜치를 새로 만든 경우, PR 올리기
   - PR은 remote ↔️ remote 이기에 Git이 아닌 GitHub의 기능이다!

---

# 이미 존재하는 Repository와 독립적으로 작업하기

1. 프로젝트 fork뜨기
2. fork뜬 프로젝트를 clone받기
3. 이하 앞 장표와 동일

---

# Caveats(1)

기억할 것: **Git은 애매한 상황에서 사용자에게 권한을 위임한다.**

1. 아직 송장이 붙지 않은 상자가 브랜치 바꾸기가 불가능하다
   - 모든 내용을 commit한 상태여야 브랜치를 바꿀 수 있다
   - ???: 아니 임시로 어디에 보관해두면 안되나?
   - `git stash`: 임시로 보관하기
   - `git stash list`: 임시로 보관한 리스트 조회
   - `git stash pop`: 임시로 보관한 것 꺼내오기

---

# Caveats(2)

2. 아직 송장이 붙지 않은 물건들이 있다면 pull이 불가능하다
   - 덮어씌워야할지, 그대로 보존해야할지를 모르니까..!
   - 커밋을 전부 마치고 pull을 하자

---

# Caveats(3)

3. 일반적으로 pull을 받아와야 push가 가능하다.
   - 만약 내 내용이 옳다고 생각된다면, `git push --force`로 강제로 밀어버려도 된다

---

# 6. git의 내부원리

---

# git의 내부원리

- 저장소의 수많은 정보들(remote, local, branch, history...)는 대체 어디에 저장되어있는걸까?
- 저장소 내 `.git`에 비밀이 있다

---

# .git

<div style="display: flex; gap: 20px;">
    <img src="/images/git-internal.png" alt=""/>
    <ul>
        <li><code>HEAD</code>: 내가 지금 history상의 어느 지점에 있는지를 알려주는 cursor</li>
        <li><code>config</code>: git 관련 설정</li>
        <li><code>index</code>: staging 관련 정보</li>
        <li><code>objects</code>: history를 이루는 hash들의 정보</li>
        <li><code>refs</code>: branch들의 정보</li>
    </ul>
</div>

---

# Hash value

- hash: 잘게 쪼개서 새로운 무언가를 만드는 것
- 결과물: hash value, hash code, hash checksum, ...
<div style="display: flex; align-items: center; margin-top: 30px">
    <img src="/images/hashbrown.png" width="300" alt=""/>
</div>

---

# Hash value

<div style="margin-bottom: 20px;">
    <ul>
        <li>파일의 내용과 메타데이터 ➡️ sha1 해싱 ➡️ deflate 알고리즘으로 압축</li>
        <li>커밋한 시점의 snapshot을 해쉬값으로 남겨놓는다</li>
        <li>이러한 snapshot들을 이용해 기록조작이 가능하다!</li>
    </ul>
</div>

```python
print('hello world')

# hash: 8b8d0064cdef7af5e2aadb3cdcd7b7606bb3fd68
```

<div style="margin-top: 20px;">
    <ul>
        <li><code>git log</code>: 로그보기</li>
        <li><code>git show &lt;HASH&gt;</code>: 변경사항 보기</li>
        <li><code>git cat-file -p &lt;HASH&gt;</code>: 메타데이터 보기(부모, 저자 등등)</li>
    </ul>
</div>

---

# 7. 개념3) 기록 조작하기

---

# 기록 조작하기

- 작업을 하다보니 일정 시점으로 다시 작업물을 되돌리고 싶어졌다. 일일이 `Ctrl + z`해야할까?

---

# HEAD

- 현재 내가 commit history의 어느 부분에 위치하는가에 대한 정보
- 프로그래밍언어에서의 reference/pointer 개념으로 이해하면 좋다

<div style="display: flex; align-items: center; margin-top: 30px">
    <img src="/images/head-example.png" width="300" alt=""/>
</div>

---

# 명령어 요약

- `git revert <hash>`: 맘에 안드는 commit을 되돌리고 싶을 때. 되돌린다는 commit 자체가 남는다
- `git reset --hard <hash>`: 기록을 아예 날려버리고 싶을 때. 혹시 모르니 백업은 해놓자^^;
- `git reset --soft <hash>`: 기록을 조작할 생각은 없고 HEAD를 왔다갔다만 하고 싶을 때

---

# rebase

- `rebase`: base를 다시(re) 바꾼다.
- 노드의 부모를 바꾸는 기법
- commit history를 일자로 깔끔하게 유지할 수 있다.
- 이런게 있구나 정도로 이해해도 됩니다.

<div style="display: flex; align-items: center; gap: 30px; margin-top: 40px">
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/rebase-merge.png" width="400" alt=""/>
    </div>
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/recursive-merge.png" width="400" alt=""/>
    </div>
</div>

---

# 8. GitHub 메뉴 소개

---

# 나도 예쁜 깃허브 프로필을 갖고싶다!

<div style="display: flex; align-items: center; margin-top: 30px; gap: 10px">
    <img src="/images/pretty-github-readme.png" width="400" alt=""/>
</div>

---

# 꾸미는 법

- 본인 이름으로 된 Repository만들기
- 마크다운으로 글 작성하기
- 예쁘게 꾸며보자(https://github.com/jinoov-sandbox/awesome-readme.git)

---

# Organization을 만들어보자

- 조별과제를 한다치면, 우리조만의 공간이 있으면 좋지 않을까?

<div style="display: flex; align-items: center; margin-top: 30px; gap: 10px">
    <img src="/images/tensorflow.png" width="400" alt=""/>
</div>

---

# 9. 외부도구와 연동하기

---

# System Integration

1. Slack에 깃허브 연동하기
2. 나만의 웹사이트 만들어서 자동배포하기

<div style="display: flex; align-items: center; margin-top: 30px">
    <img src="/images/system-integration.png" width="300" alt=""/>
</div>

<div style="color: #c1c1c3; font-weight: 500; font-size: 14px; margin-top: 40px">
    <p style="margin: 0;">외부 서비스들 연동과 관련한 방법들은 절대 외울 필요가 없으며, 외부 메뉴얼 보고 따라하는게 전부입니다.</p>
    <p style="margin: 0;">왜 이걸 연동하는지에 관한 문제의식에 집중해주세요.</p>
</div>

---

# Slack에 깃허브 연동하기

- "Issue 생성할 때마다, PR 날릴 때마다.. 일일이 보고해야하나?? 🤔"
- [레포지토리](https://github.com/jinoov-sandbox/my-awesome-website)
- [참고링크](https://sepiros.tistory.com/37)

<div style="display: flex; align-items: center; margin-top: 30px">
    <img src="/images/integration-in-slack.png" width="300" alt=""/>
</div>

---

# 나만의 웹사이트 만들어서 자동배포하기

- 배포(업로드) 지옥에서 벗어나자
- [참고링크](https://shape-coding.tistory.com/entry/Vercel-Vercel%EB%A1%9C-%ED%94%84%EB%A1%A0%ED%8A%B8-%EB%B0%B0%ED%8F%AC%ED%95%98%EA%B8%B0)

<div style="display: flex; align-items: center; margin-top: 15px; gap: 100px">
    <img src="/images/kakao-talk.jpeg" width="180" alt=""/>
    <img src="/images/server-upload.png" width="300" alt=""/>
</div>

---

# 좋은 파이프라인을 만들자

<div style="display: flex; align-items: center;">
    <img src="/images/cycle.png" width="400" alt=""/>
</div>

---

# 마무리하며

- Git은 직접 많이 써봐야 늡니다. 프로젝트할 때 꼭꼭 써보시고, SW 관련 과제할 때라도 깃을 꼭 써보세요!
- 명령어는 구글과 GPT가 다 알려주기에, 머릿속에 큰 그림을 그리는게 제일 중요하고, 이를 위해 여러 사람의 관점을 배우는게 좋습니다.
  - [코딩애플 git 무료강의](https://codingapple.com/course/git-and-github/)
  - [드림코딩 git 무료강의](https://www.youtube.com/watch?v=Z9dvM7qgN9s)
- 피드백과 질문은 언제나 환영이에요. 들어주셔서 감사합니다 :)
