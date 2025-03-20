# mr2.github.io
Documentation for MR2's URC project

This link is our site:
https://urc-kaist.github.io/mr2.github.io/

# URC-KAIST 웹사이트

## 로컬 개발 환경 설정

1. Python 가상환경 생성 및 활성화
```bash
python3 -m venv venv
source venv/bin/activate  # macOS/Linux
```

2. 필요한 패키지 설치
```bash
pip install -r requirements.txt
```

3. 문서 빌드
```bash
make html
```

4. 브라우저에서 확인
```bash
open _build/html/index.html  # macOS
```

## 공동 작업 가이드

1. 새로운 브랜치 생성
```bash
git checkout -b feature/your-feature-name
```

2. 문서 수정
- RST 파일 수정 (`*.rst`)
- 이미지는 `_images/` 디렉토리에 저장
- 템플릿은 `_templates/` 디렉토리에서 수정

3. 로컬 테스트
```bash
make html
open _build/html/index.html
```

4. 변경사항 커밋
```bash
git add .
git commit -m "설명적인 커밋 메시지"
```

5. Pull Request 생성
- GitHub에서 Pull Request 생성
- PR 템플릿에 따라 내용 작성
- 변경사항 설명 및 스크린샷 첨부

## 디렉토리 구조
- `index.rst`: 메인 페이지
- `sections/`: 각 섹션별 문서
- `_images/`: 이미지 파일
- `_templates/`: 페이지 템플릿
- `_static/`: 정적 파일 (CSS, JS 등)
