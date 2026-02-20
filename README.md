# 미정

---

## 팀원
추후에 추가예정

---

## 개발 규칙
### 변수 네이밍
- 변수: `snake_case`
- 클래스: `PascalCase`
- 상수: `UPPER_CASE`
- DataFrame: `_df`
  > 예: user_df, sample_df

---

###  폴더 구조
```
project/
|
├─── data/              # 데이터 셋
├─── JoDongHwi          # 개인 작업폴더 (예시)
├─── requirements.txt   # pip 관리 파일
├─── LICENSE            # MIT 라이센스
├─── .gitignore
└─── README.md
```
> 개인 작업 공간은 폴더 명을 파스칼 케이스로 생성

---

### git commit convention
- feat: 새로운 기능
- fix: 버그 수정
- chore: 설정 변경
- docs: 문서 수정

---

### 커밋 메시지 작성 규칙

본 프로젝트는 Conventional Commits 규칙을 따릅니다.

- 커밋 제목(head)은 반드시 영어로 작성합니다.
- 커밋 타입은 소문자(feat, fix, chore, docs, refactor 등)를 사용합니다.
- 제목은 72자 이내로 간결하게 작성합니다.
- 필요할 경우 커밋 본문(body)에 한국어 설명을 추가할 수 있습니다.
- 이슈가 있는 경우 커밋 메시지에 이슈 번호를 함께 명시합니다. (예: #12)

### 작성 형식

<type>(scope): 간단한 요약

예시:
```git

git commit -m "docs(README): add project rules

팀 프로젝트 규칙을 README에 정리함

Refs: #0"
```
