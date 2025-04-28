# Git

## 1. Git 프로그램 설치

- 프로그램 다운로드: https://git-scm.com
- 64-bit Git for Windows Setup 설치

## 2. Git 버전 확인

- 윈도우 키보드 + R 키보드 : `cmd` 입력

```bash
    git --version
```

- 출력창 확인

## 3. VSCode 에 Git 설정하기

### 3.1. 터미널 환경을 git bash 로 설정하기

- 윈도우, 맥, 리눅스 의 명령창을 통일하기 위함.
- 관리도구 선택 > 설정메뉴 선택
- 설정화면 > `default:Windows` 입력
- `Git Bash` 선택
- 설정화면 닫고, VSCode 재실행 추천

### 3.2. VSCode 에서 Git 옵션 설정하기

- 터미널 실행 : `Ctrl + 백틱` 추천
- git 버전 확인

```bash
git --version
```

- 기본 브랜치명을 `main` 으로 설정

```bash
git config --global init.defaultBranch main
```

- 윈도우, 맥, 리눅스 환경에서 Enter 키 처리를 통일함.

```bash
git config --global core.autocrlf true
```

- 깃 Commit 명령을 VSCode 에서 작성하도록 설정

```bash
git config --global core.editor "code --wait"
```

- 깃 사용자 아이디 설정하기

```bash
git config --global user.name "아이디"
```

- 깃 사용자 아이디 확인하기

```bash
git config --global user.name
```

- 깃 사용자 이메일 저장하기

```bash
git config --global user.email "이메일"
```

- 깃 사용자 이메일 확인하기

```bash
git config --global user.email
```

## 4. 깃 작업하기(실습)

### 4.1. 깃 프로젝트 관리 초기화 하기

- 현재 폴더에 Git이 추적할 수 있는 '버전 관리 폴더'로 만드는 것
- .git이라는 숨겨진 폴더가 생성돼서,
- 그 안에 Git이 필요한 데이터(버전 기록, 설정 등)를 저장.

```bash
git init
```

### 4.2. 깃 현재 상태 파악하기

```bash
git status
```

### 4.3. 깃 현재 수정된 파일, 폴더 등을 저장하기

- 원하는 파일만 저장하기

```bash
git add README.md
```

- 모든 파일 및 폴더 저장하기(추천)

```bash
git add .
```

### 4.4. 수정 내역 메모 남기기

- 한줄 작업 메모

```bash
git commit -m "깃 작업 관련 설명글작성"
```

- 여러 줄 메모 작성하기 (제목, 상세내용)

```bash
git commit
```

### 4.5. 커밋 내용 컨벤션 알아보기

```bash
[커밋타입] : 커밋 메시지(옵션)
```

- 커밋 타입 : 작업의 분류
- 옵션 : 이슈 또는 수정이 된 작업커밋 번호 또는 추가정보
- 커밋 메시지 : 무엇을 했는지 짧은 내용

#### 4.5.1. 커밋타입

- `[feat]` : 새로운 기능 추가
- `[fix]` : 버그 수정
- `[docs]` : 문서 수정(README.md)
- `[style]` : 코드의 스타일 변경(띄워쓰기, 세미콜론 등)
- `[refector]` : 코드 리팩토링(기능 변경, 코드 정리 등)
- `[test]` : 테스트 코드 추가
- `[chore]` : 기타 (빌드 설정, 패키지 업데이트 등)

#### 4.5.2. 옵션

- 만약 `회원가입 로그인 기능 추가` 라면
- 아래는 이슈 #23 번을 해결하고 기능을 추가했다는 것

```
[feat]:회원가입 로그인 기능 추가(#23)
```

#### 4.5.3. 커밋 내용

- Enter 키를 기준으로 제목과 내용을 구분합니다.

```
[docs] : 커밋 제목

커밋 상세 내용작성

```

### 4.6. 커밋 내용 확인하기

- 기존의 commit 된 내용을 확인하기
- 상세보기

```bash
git log
```

- 간략하게 보기

```bash
git log --oneline
```

- 하나의 commit 상세보기

```bash
git show 커밋아이디
```

### 4.6.1. 각 항목 관련 사항 이해하기

- commit : 고유한 커밋 번호(아이디)
- Author : 작성자
- Date : 날짜
- 메시지 : 상세 내용

### 4.7. 브랜치 작업해 보기

- `나뭇가지` 라는 의미로 원 줄기로 부터 파생되는 것을 말함.
- 원 `소스`로 부터 파생한 새롭게 `분기한 소스` 관리를 말함.
- `브랜치를 생성시에는 add 와 commit 이 완료되어야 함.`

#### 4.7.1. 브랜치 생성하기

```bash
git add .
git commit -m "[docs]:브랜치 실습 test 생성하기"
git branch test
```

#### 4.7.2. 브랜치 목록보기

```bash
git branch -v
```

#### 4.7.2. 브랜치 이동하기

```bash
git switch test
```

#### 4.7.3. 브랜치 삭제하기

```bash
git branch -D test
git branch -v
```

#### 4.7.4. 브랜치 합치기

- 브랜치를 하나로 합쳐주기
- 주의 사항 : `main 브랜치에서 test 브랜치 합쳐줄 겁니다.`

```bash
git add .
git commit -m "[docs]:브랜치 실습 test 합치기"
```

```bash
git merge 합쳐주고자하는 브랜치명
```

### 4.8. 깃 브랜치 충돌 해결해 보기

- 깃 브랜치를 merge 하면 많이 발생합니다.

```
<결과물>
main  >> 242라인  - (테스트중~) 나는 main에서 계속 작업을 하고 있었습니다.
login >> 242라인  - (테스트용)`login 브랜치`에서 나는 로그인 기능을 구현했다.


merge ▼
현재 브런치에서 바뀐거 적용할래? / 머지 하려고하는거 바뀐내용 적용할래? / 둘다 적용할래? / 네가 수정해서 적용1할래?
4가지 선택사항중에 원하는걸로 선택하면된다.(아래는 양쪽 다 살린경우)


main >>
242라인  - (테스트중~) 나는 main에서 계속 작업을 하고 있었습니다.
243라인  - (테스트용)`login 브랜치`에서 나는 로그인 기능을 구현했다.

```

- 선택 후 merging 중을 commit 해서 적용해놓는다.

# GitHub

## 1. GitHub 회원가입하기

- https://github.com

## 2. GitHub 프로젝트(Repository) 생성하기

- 만약 til_git 프로젝트 생성했다면 Git_hub 에도 동일하게 생성하자.
- public으로 셋팅 : 외부로 소스 공개
- description 은 작성해 주자 : 프로젝트 설명

## 3. GitHub 인증하기

### 3.1. 무조건 GitHub에 로그인 된 상태로 시도하셔야 합니다.

### 3.2. `윈도우 > 자격 증명 관리자 > Window 자격 증명` 에서 github 확인

- 기존에 로그인이 되어있다면 삭제 후 새로 생성할 것
- PC 정리 또는 자리 이동 시 반드시 삭제하셔야 합니다.

## 4. GitHub 프로젝트 연결하기

- 온라인페이지에서 new repository 생성 후 뜨는 설명문을 실행한다.

```bash
echo "# til_git" >> README.md
```

- 리눅스명령어 : til_git 폴더만들고 readme.md 파일을 만들어라

### 4.1. 원격 저장소 주소 지정하기

- `remote` 는 원격(인터넷)을 말한다
- `add`는 추가하라
- `origin`
  └ http 주소를 간략하게 별칭해 준 것
  └ 다른별칭해도되지만 통상적으로는 origin
  └ `원격 이름`을 말함

```bash
git remote add origin https://github.com/아이디/til_git.git

```

### 4.2. 원격 저장소 목록 보기

```bash
git remote -v
```

### 4.3. 원격 저장소에 소스 등록하기

- 습관적으로 하면 좋은 작업! (crtl + s 즉 저장 후)
- 현재 저장되어있는 내역만 웹에 업로드된다.

```bash
git add .
git commit -m "[docs]:최초등록"

git push -u origin main
```
