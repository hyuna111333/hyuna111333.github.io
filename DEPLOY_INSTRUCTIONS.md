# GitHub Pages - 배포 안내

아래 단계 중 하나를 선택해 배포하세요. (파일들은 로컬에서 한 폴더에 넣어두고 진행)

## A. GitHub 웹 UI로 업로드 (간단)
1. GitHub에 로그인 후 새 저장소 생성
   - 저장소 이름: 원하는 이름 (예: `my-site`)  
   - 만약 루트 도메인으로 사용하려면 저장소 이름을 `hyuna111333.github.io`로 지정하세요.
2. 생성한 저장소 페이지에서 "Add file" → "Upload files" 선택.
3. index.html, .nojekyll, DEPLOY_INSTRUCTIONS.md, README.md 그리고 asset 폴더(있다면 css/, js/, images/)를 드래그 앤 드롭하여 업로드 → Commit changes.
4. 저장소의 Settings → Pages로 이동하여 Source를 `main` branch / root (/)로 설정.
5. 몇 분 후에 생성된 URL에서 사이트 확인:
   - 루트 저장소(`hyuna111333.github.io`)인 경우: `https://hyuna111333.github.io/`
   - 일반 저장소인 경우: `https://hyuna111333.github.io/REPO_NAME/`

## B. 로컬에서 git 사용 (추천 — 버전 관리 용이)
로컬에서 작업 폴더(파일들 위치)에서 아래 명령을 실행하세요。

```bash
# 1) 초기화 및 커밋
git init
git add .
git commit -m "Initial site commit"

# 2) 원격 저장소 연결 (아래 URL을 본인의 저장소 URL로 바꿔주세요)
git branch -M main
git remote add origin https://github.com/hyuna111333/hyuna111333.github.io.git

# 3) 푸시
git push -u origin main
```

푸시 후 GitHub에서 Settings → Pages로 가서 Branch를 `main` / Folder를 `/ (root)`로 설정하면 배포가 시작됩니다。

### 예: 루트 URL로 사용하려면
- 저장소 이름을 `hyuna111333.github.io`로 만들고 위의 origin URL을 
  `https://github.com/hyuna111333/hyuna111333.github.io.git` 로 설정하세요.
- 푸시 후 `https://hyuna111333.github.io/` 에서 바로 접근됩니다。

## ZIP 만들기 (Windows)
- 파일 탐색기에서 사이트 루트 폴더를 우클릭 → 보내기(Send to) → 압축(ZIP) 폴더
- 또는 PowerShell:
```powershell
Compress-Archive -Path "C:\path\to\site\*" -DestinationPath "C:\path\to\site.zip"
```

## 이미지/자원 관련 주의사항
- index.html 내부에서 file:///C:/... 같은 로컬 경로가 사용되어 있으면 GitHub Pages에서 로드되지 않습니다. (지금 제공하신 index.html에는 로컬 file:// 경로가 없습니다.)
- 이미지가 있다면 `images/` 폴더를 만들어 상대경로(`./images/your.png` 또는 `images/your.png`)로 참조하세요。
- 외부 CDN 사용(예: Tailwind, Google Fonts)은 자유롭게 사용 가능합니다。

## 문제 해결 팁
- 이미지/파일 404: 브라우저 콘솔(F12)에서 요청 경로 확인 → 파일 구조와 경로를 맞춰 수정하세요。
- 캐시 문제: 변경 후 새로고침(Shift+F5) 또는 캐시 무시 새로고침 사용。