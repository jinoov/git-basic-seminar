---
theme: seriph
themeConfig:
  primary: '#3182f6'
  fontWeight: 500
class: text-center
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: Git Basic Seminar 
mdc: true
fonts:
  sans: 'Noto Sans KR'
  local: 'Noto Sans KR'
image: 'https://unsplash.com/ko/%EC%82%AC%EC%A7%84/HLQDfaJUTVI'
---

# Git/GitHub 101 

--- 

# 발표자 소개
- 산업공학과 19학번 최진호
- 인지과학 복수전공
- 스타트업에서 2년동안 웹개발자로 근무
- 생산성(~~날먹~~), UX 엔지니어링에 관심이 많음

--- 

# Table Of Contents

1. Git이란? 대체 왜 쓰는가?
2. Git 관련 도구들 소개(CLI & GUI)
3. 개념1) Local and Remote
4. 개념2) 작업공간 분리와 협업하기
5. 개념3) 기록조작하기
6. System Integration

---

# 1. Git이란?

<ul>
    <li>리눅스 토발즈라는 매우 똑똑한 프로그래머가 만든 <b>분산형 버전 관리 시스템</b></li>
    <li>분산 == 협업</li>
    <li>버전 -> 기록</li>
    <li style="color: red; font-weight: 700">협업을 용이하게 하는 프로그램 기록 관리 시스템</li>
</ul>

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/git-logo.png" width="150" alt="">
    <p style="color: #666; font-size: 14px">Global Information Tracker(?)</p>
</div>

---

# 1. Git을 대체 왜 쓰는가?(문제의식)

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
    <h4>그러나...</h4>
    <ul>
        <li>누구 한명이 실험적인 시도를 하고 싶다면?</li>
        <li>실시간 변경은 늘 옳을까?</li>
    </ul>
</div>


<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/google-slide.png" width="500" alt=""/>
</div>

---

# 2. Git 관련 도구들

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

# CLI vs GUI
- 더 세밀하게 조작하고자 한다면 CLI
- 외부 서버에 붙어서 작업하고 싶다면 CLI
- 일반적인 작업 + 개념이해에는 GUI로도 충분!
 
<div style="display: flex; align-items: center; gap: 20px; margin-top: 40px">
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/github-desktop.png" width="100" alt=""/>
    </div>
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/sourcetree.png" width="100" alt=""/>
    </div>
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/fork.png" width="100" alt=""/>
    </div>
</div>

---

# Remote 저장소
- 그래서 내 소스를 어디에 올릴까?

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
- 가장 근본이 되는 저장소 == origin

---

#  3. 개념1) Local and Remote
<div style="margin-top: 40px">
    <img src="/images/local-and-remote.png" width="300" alt=""/>
</div>

---

# Layers in Local 
<div>
    <ul>
        <li>History: 변동 기록</li>
        <li>Staged: 상자 안의 영역</li>
        <li>Unstaged: 상자 밖의 영역</li>
        <li>Untracked: 아예 관심을 갖지 않는 영역</li>
    </ul>
    <p style="margin-top: 20px; text-decoration: line-through">굳이 이렇게까지 복잡하게 해야하는가?</p>
</div>
---

# Layers in Local
<div>
    <img src="/images/local-layers.png" alt="">
</div>

---

# Remote의 변경사항 내려받기
- Question.
- 내려받은 내용이 작업내용을 덮어씌운다면..?
 
---

# Remote의 변경사항 내려받기
- Answer.
- Git은 애매한 상황에서는 사용자에게 권한을 위임한다
- 충돌이 덜 나게하려면? 
 
<div style="margin-top: 40px">
    <img src="/images/woowahan-comment.png" width="600" alt=""/>
    <p style="font-size: 12px; color: #6e6e6e">Reference: 우아한기술블로그 - 우린 Git-flow를 사용하고 있어요</p>
</div>
---

# 명령어 요약
- `git status`: staging area / unstaging area 확인
- `git add <원하는 파일>`: 변경 사항들을 상자 안에 넣는다 
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

#  4. 개념2) 작업공간 분리와 협업하기
- 만약 두 사람이 하나의 remote를 바라보고 있다면?
<div style="display: flex; align-items: center; margin-top: 20px">
    <img src="/images/one-remote-two-locals.png" width="300" alt=""/>
</div>

---

# 작업공간 분리하기
- 작업공간을 분리함으로써 독립성을 확보하기
<div style="display: flex; align-items: center; margin-top: 20px">
    <img src="/images/separate-workspace.png" width="400" alt=""/>
</div>

---

# 명령어 요약
- `git branch`: 브랜치 리스트 보기
- `git branch -c <브랜치명>`: 브랜치만들기 
- `git branch -d <브랜치명>`: 브랜치없애기 
- `git switch(checkout) <브랜치명>`: 브랜치 변경하기

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

# 딴소리) git의 원리
- 저장소의 수많은 정보들(remote, local, branch, history...)는 대체 어디에 저장되어있는걸까?
- 저장소 내 `.git`에 비밀이 있다

---

# Hash value

