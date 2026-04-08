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

- **내장사전 활용** — 수준별 내장사전 (미취학~일반, 초급/중급/고급)
- **일상/실용** — 일상생활, 여행, 비즈니스 영어
- **시험대비** — 수능, TOEIC, TOEFL, IELTS, 공무원, 편입

## 참고

- `wordCount`는 실제 `words` 배열 길이와 다소 차이가 있는 파일이 존재한다.
- `sample_words.json`은 테스트용이며 `preset_list.json`에 등록되어 있지 않다.
