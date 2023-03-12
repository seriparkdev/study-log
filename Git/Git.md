### 📌WORKFLOW

#### **LOCAL**

- **`working directory`**

  프로젝트의 파일을 수정하고 작업하는 곳

  untracked : 추적되지 않는 파일

  tracked : 추적하고 있는 파일

  **→** unmodified : 수정되지 않은 상태

  **→** modified : 수정된 상태 staging area로 이동 가능

- **`staging area`**
  버전 히스토리에 저장할 준비가 되어있는 파일을 저장하는 곳
- **`.git directory(local repo)`**
  버전의 히스토리를 가지고 있는 곳
  개인저장소

#### REMOTE

- **`remote repo`**
  원격 저장소
  </br>

---

### 📌 COMMAND

#### [Git의 모든 명령어](https://git-scm.com/docs)

- **git `add`**

  파일을 staging area로 이동

  git `add` `*` : .gitignore(업로드 하거나 관리하지 않을 파일) 파일에 있는 파일도 staging area로 옮기기

  git `add` `.` : .gitignore 파일을 제외하고 staging area로 옮기기

- **git `commit`**

  staging area의 변경사항을 .git directory로 옮김

  git `commit` `-m` `""` : 메세지를 붙여 커밋

  _의미있는 이름 사용 너무 크거나 작은 단위로 커밋X
  각각의 커밋은 해쉬태그를 가져 버전 정보 참조 가능_

- **git `push`**

  로컬 저장소에서 원격 저장소로 저장

- **git `pull`**

  원격 저장소에서 로컬 저장소로 저장

- **git `checkout`**

  파일을 working directory로 데려옴

- **git `init`**
  .git(로컬 저장소) 생성

- **Git`config` `--list`**
  설정 확인

- **`alias`**
  명령어를 원하는 별명으로 부를 수 있음. 단축키.

- **git `rm`**
  git `rm` `-rf` : 파일 삭제
  git `rm` `--cached` : staging area에서 wokring directory로 파일을 옮김

- **git `diff`**
  수정 사항 확인

- **git `log`**
  이력 확인
- **git `reset`**
  이력 제거. 원하는 이력으로 완전히 되돌아 감.
- **git `revert`**
  reset보다 안전한 방법. 상태를 유지하고 이력 되돌아 가기.
- **git `merge`**
  브랜치 합침. 내용 병합.
- **git `remote`**

  git `remote` `rm` : 설정된 원격 저장소 삭제

  git `remote` `add` `origin` : 원격 저장소 설정

- **git `branch`**

  git `branch` `-M` `main` : 브런치 선택
  </br>

---

### 📌 CLONE -> PUSH

```
1. git clone url  - 클론
2. git remote add origin url - 파일을 저장할 repo url 설정
3. git push -u origin main - 업로드
```
