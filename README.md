# We moved to https://github.com/URC-kaist/urc-kaist.github.io



# ~~URC-KAIST MR2 웹사이트~~

공식 웹사이트: https://urc-kaist.github.io/mr2.github.io/

## 시작하기 전에

### 필수 설치 항목
1. Python 3.8 이상
   - Windows: [Python 공식 웹사이트](https://www.python.org/downloads/)에서 다운로드
   - macOS: `brew install python3`
   - Linux: `sudo apt install python3 python3-pip` (Ubuntu/Debian)

2. Git
   - Windows: [Git for Windows](https://gitforwindows.org/)
   - macOS: `brew install git`
   - Linux: `sudo apt install git` (Ubuntu/Debian)

## 로컬 개발 환경 설정

### 1. 저장소 클론
```bash
git clone https://github.com/URC-kaist/mr2.github.io.git
cd mr2.github.io
```

### 2. Python 가상환경 생성 및 활성화

Windows:
```bash
python -m venv venv
.\venv\Scripts\activate
```

macOS/Linux:
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. 필요한 패키지 설치
```bash
pip install -r requirements.txt
```

### 4. 문서 빌드
```bash
# Windows
make.bat html

# macOS/Linux
make html
```

### 5. 브라우저에서 확인

Windows:
```bash
start _build\html\index.html
```

macOS:
```bash
open _build/html/index.html
```

Linux:
```bash
xdg-open _build/html/index.html
```

## 문서 수정 가이드

### 기본 섹션 수정
1. `sections` 디렉토리 내의 해당 `.rst` 파일을 수정
2. 이미지는 `_static/images/` 디렉토리에 저장

### 새로운 섹션/페이지 추가

1. 새로운 섹션 디렉토리 생성 (예: rover_2024)
```bash
mkdir sections/rover_2024
```

2. 새로운 `.rst` 파일 생성
```bash
# 메인 페이지
touch sections/rover_2024/index.rst

# 하위 페이지들
touch sections/rover_2024/mechanical.rst
touch sections/rover_2024/electrical.rst
touch sections/rover_2024/software.rst
```

3. 섹션 메인 페이지 작성 예시 (`sections/rover_2024/index.rst`):
```rst
Rover 2024
==========

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   mechanical
   electrical
   software
```

4. 상위 목차에 새 섹션 추가 (`index.rst`):
```rst
.. toctree::
   :maxdepth: 2
   :caption: Contents:

   sections/about/index
   sections/rover_2024/index  # 새로운 섹션 추가
```

### 문서 작성 팁
- 제목 표시:
```rst
큰 제목
======

중간 제목
--------

작은 제목
~~~~~~~~
```

- 이미지 추가:
```rst
.. image:: /_static/images/your_image.png
   :width: 400
   :alt: 이미지 설명
```

- 링크 추가:
```rst
`외부 링크 <https://example.com>`_
:doc:`내부 문서 링크 </sections/rover_2024/mechanical>`
```

## 변경사항 적용하기

1. 새로운 브랜치 생성
```bash
git checkout -b feature/your-feature-name
```

2. 로컬 테스트
```bash
# Windows
make.bat clean
make.bat html

# macOS/Linux
make clean
make html
```

3. 변경사항 확인
```bash
# Windows
start _build\html\index.html

# macOS
open _build/html/index.html

# Linux
xdg-open _build/html/index.html
```

4. 변경사항 커밋 및 푸시
```bash
git add .
git commit -m "자세한 커밋 메시지"
git push origin feature/your-feature-name
```

5. Pull Request 생성
- GitHub 웹사이트에서 Pull Request 생성
- 변경사항 설명 작성
- 스크린샷 첨부 (UI 변경시)
- 리뷰어 지정

## 디렉토리 구조
```
.
├── index.rst          # 메인 페이지
├── conf.py           # Sphinx 설정 파일
├── requirements.txt  # Python 패키지 목록
├── _static/         # 정적 파일 (이미지, CSS 등)
├── _templates/      # HTML 템플릿
└── sections/        # 문서 섹션
    ├── about/      # 소개 페이지
    ├── rover_2024/ # 2024년 로버 프로젝트
    └── ...
```
