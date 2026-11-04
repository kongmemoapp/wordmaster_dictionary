# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

이 저장소는 WordMaster 앱의 **단어장 관리 전용 프로젝트**이다. `presets/` 폴더의 JSON 파일들이 GitHub에 업로드되어 앱에 서비스된다. 빌드 시스템, 테스트, 애플리케이션 코드 없이 단어장 데이터만 관리한다.

## 운영 방식

1. `presets/preset_list.json` — 서비스에 제공되는 마스터 인덱스. 앱이 이 파일을 읽어 단어장 목록을 표시한다.
2. 단어장 추가 시: `temp/`에서 작업 → 완성 후 `presets/`에 배치 → `preset_list.json`에 항목 추가 → GitHub에 push.

## 디렉터리 구조

- **`presets/`** — 정식 단어장 파일 (GitHub에 업로드되어 서비스에 제공)
- **`temp/`** — 단어장 제작용 임시 작업 경로. 단어장 생성 요청 시 이 경로에서 작업하고, 완성 후 `presets/`로 이동한다.

## 파일 형식

**preset_list.json 항목:**
```json
{"file": "파일명.json", "name": "표시명", "description": "설명", "wordCount": 숫자, "category": "카테고리명"}
```

**단어장 파일:**
```json
{"name": "단어장명", "description": "설명", "words": [{"w": "english", "m": "한국어 뜻"}, ...]}
```

## 카테고리

`category` 문자열은 앱의 단어장 선택 화면에서 1단계 목록이 되며, `preset_list.json`에 처음 등장한 순서대로 표시된다. 이름 규칙은 "영역 - 세부"이다.

- **영단어 - 수준별** — 미취학 100/200/300 → 초등 800 → 중1·2·3 각 500 → 고등 입문 300 → 중고 1800 → 전문 400 → 전체 3000
- **영단어 - 시험대비** — 수능, TOEIC, TOEFL, IELTS, 공무원, 편입
- **영단어 - 일상/실용** — 일상생활, 여행, 비즈니스
- **영문법 예문 - 초등 / 중학 / 고등 / 주제별** — `w` 예문, `m` "[세부 분류] 해석 (포인트)"
- **영문법 빈칸연습** — `type: fill_in_blank` 형식 (w에 `[]` 빈칸 하나, m 정답, t 해석, explanation, choices 10개)
- **국어** — 순우리말 등
- **한자/사자성어** — 한자 급수(8급~4급), 사자성어
- **과학/상식** — 주기율표, 세계 수도 등
- **일본어** — 히라가나, 카타카나, 기초 단어
- **취미/문화** — 건담 모빌슈트 등 취미·대중문화 콘텐츠 (목록 맨 끝)

## 제작 규칙

- 일반 단어장의 `m`에는 `w`(정답)가 포함되면 안 된다. 앱 퀴즈가 `m`을 지문·보기로 쓰기 때문이다. 예시 단어에 정답이 들어가면 □로 가린다(한자 단어장 참고).
- 새 단어장은 `temp/`에서 생성 → 검증(개수, 중복, 정답 노출) → `presets/`로 이동 → `preset_list.json`에 해당 카테고리 위치에 삽입한다.

## 참고

- `wordCount`는 실제 `words` 배열 길이와 다소 차이가 있는 파일이 존재한다.
- `sample_words.json`은 테스트용이며 `preset_list.json`에 등록되어 있지 않다.
