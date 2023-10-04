---
theme: seriph
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
---

# Git/Github Basic Seminar 
깃/깃허브 입문 세미나

--- 

# 세미나장 소개
- 산업공학과 19학번 최진호
- 인지과학 연계전공
- 스타트업에서 2년동안 웹개발자로 근무
- 생산성(~~날먹~~), UX 엔지니어링에 관심이 많음

--- 

# Table Of Contents

1. Git이란? 대체 왜 쓰는가?
2. Git 관련 도구들 소개(CLI & GUI)
3. 개념1) local and remote
4. 개념2) 작업공간 분리와 협업하기
5. 개념3) 기록조작하기
6. System Integration

---

# 1. Git이란?

<ul>
    <li>리눅스 토발즈라는 매우 똑똑한 프로그래머가 만든 <b>분산형 버전 관리 시스템</b></li>
    <li>분산 -> 협업 && 버전 -> 기록</li>
    <li style="color: red; font-weight: 700">협업을 용이하게 하는 프로그램 기록 관리 시스템</li>
</ul>

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/img_1.png" width="150">
    <p style="color: #666; font-size: 14px">Global Information Tracker(?)</p>
</div>

---

# 1. Git을 대체 왜 쓰는가?(문제의식)

- 조별과제 PPT를 만들 때를 상상해보자.
- 아래 방식의 문제는 무엇일까?

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/img_2.png" width="300"/>
</div>

--- 

# 조별과제의 어려움 

<ol>
    <li>Timeline과 변동사항을 알기 힘들다.</li>
    <li>여러 사람이 함께 협업한다면, 결국 <b style="color: red">수동으로</b> 병합하는 과정이 필요하다.</li>
    <li>???: 런어스에 제출하셨나요?</li>
</ol>

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/img_2.png" width="300"/>
</div>

--- 

# 구글 슬라이드

<ul>
    <li>대안이 될 수 있는 도구: Google Slide</li>
    <li>변동사항의 파악이 용이</li>
    <li>변경사항이 자동으로 병합됨</li>
</ul>

<div style="padding: 10px; margin-top: 20px;">
    <img src="/images/img_3.png" width="500"/>
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
    <img src="/images/img_3.png" width="500"/>
</div>

---

# 발상의 전환
- Local and Remote
- 작업공간 분리하기
- 기록조작하기

---

# 2. Git 관련 도구들

<div style="display: flex; align-items: center; gap: 20px">
    <div>
        <p>CLI: Command Line Interface</p>
        <img src="/images/img_4.png" width="300"/>
    </div>
    <div>
        <p>GUI: Graphic User Interface</p>
        <img src="/images/img_5.png" width="300"/>
    </div>
</div>

---

# CLI vs GUI
- 더 세밀하게 조작하고자 한다면 CLI
- 외부 서버에 붙어서 작업하고 싶다면 CLI
- 일반적인 작업 + 개념이해에는 GUI로도 충분!
 
<div style="display: flex; align-items: center; gap: 20px; margin-top: 40px">
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/img_6.png" width="100"/>
    </div>
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/img_7.png" width="100"/>
    </div>
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/img_8.png" width="100"/>
    </div>
</div>

---

# Remote 저장소
- 그래서 내 소스를 어디에 올릴까?

<div style="display: flex; align-items: center; gap: 20px; margin-top: 40px">
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/img_9.png" width="100"/>
    </div>
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/img_10.png" width="100"/>
    </div>
    <div style="border-radius: 20px; overflow: hidden">
        <img src="/images/img_11.png" width="100"/>
    </div>
</div>

---

#  3. 개념1) local and remote

---

#  4. 개념2) 작업공간 분리와 협업하기
