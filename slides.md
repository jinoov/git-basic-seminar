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
- UI/UX에 대한 관심으로 인지과학 연계전공
- 웹 에이전시 및 스타트업에서 2년동안 Web Front-End Engineer로 근무
- 생산성, 좋은 워크플로우, GraphQL 같은 날먹가능한 기술들에 관심이 많음

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
    <img src="/img_1.png" width="150">
    <p style="color: #666; font-size: 14px">Global Information Tracker(?)</p>
</div>

---

# 1. Git을 대체 왜 쓰는가?(문제의식)

- 조별과제 PPT를 만들 때를 상상해보자.
- 아래 방식의 문제는 무엇일까?

<div style="padding: 10px; margin-top: 20px;">
    <img src="/img_2.png" width="300"/>
</div>

--- 

# 1. Git을 왜 쓰는가?

<ul>
    <li>Timeline과 변동사항을 알기 힘들다.</li>
    <li>여러 사람이 함께 협업한다면, 결국 <b style="color: red">수동으로</b> 병합하는 과정이 필요하다.</li>
    <li>???: 런어스에 제출하셨나요?</li>
</ul>

<div style="padding: 10px; margin-top: 20px;">
    <img src="/img_2.png" width="300"/>
</div>

--- 

# 1. Git을 왜 쓰는가?

- 대안이 될 수 있는 도구
- Google Slide

<div style="padding: 10px; margin-top: 20px;">
    <img src="/img_3.png" width="500"/>
</div>
