# Project ED

Unity **6000.3.10f1** 프로젝트입니다.

## 프로젝트 받기

1. 최신 커밋을 clone/pull하거나 GitHub의 **Code → Download ZIP**으로 받습니다.
2. ZIP은 압축을 완전히 푼 뒤, Unity Hub에서 `Assets`, `Packages`, `ProjectSettings`가 있는 폴더를 엽니다.
3. Unity **6000.3.10f1**로 열어 패키지 설치와 에셋 임포트가 끝날 때까지 기다립니다. 패키지 중 Git URL 의존성이 있으므로 Git도 설치되어 있어야 합니다.
4. `Assets/Scenes/SampleScene.unity`를 열고 Play를 누릅니다.

이미지(`.png`), 폰트(`.ttf`), 기획서(`.pdf`)는 실제 파일을 일반 Git으로 저장합니다. 현재 포함된 에셋을 받는 데 Git LFS는 필요하지 않습니다. 다른 확장자는 `.gitattributes`의 LFS 규칙이 남아 있으므로, 추후 해당 형식의 에셋을 추가할 때는 Git LFS 설치 및 원본 업로드가 필요합니다.

## 이미지가 흰 사각형으로 보이는 경우

이전 커밋은 PNG와 폰트를 Git LFS로 저장했습니다. LFS 원본을 받지 못하면 `.png`라는 이름의 파일 안에 이미지 대신 아래와 같은 텍스트만 들어 있습니다.

```text
version https://git-lfs.github.com/spec/v1
oid sha256:...
size ...
```

Unity가 이 파일을 이미지로 임포트하지 못하면 UI의 위치와 텍스트는 남아 있어도 이미지가 흰 사각형으로 보일 수 있습니다. `.meta` 파일을 삭제하거나 이미지 참조를 다시 지정할 필요는 없습니다.

- **권장:** 이 수정이 포함된 최신 커밋을 받고 Unity에서 다시 임포트합니다. ZIP으로 받았다면 기존 폴더에 덮어쓰기보다 새 폴더에 풀어 여는 것이 확실합니다.
- **이전 커밋을 계속 사용할 경우:** Git clone한 프로젝트 폴더에서 아래 명령으로 LFS 원본을 받은 후 Unity로 돌아가 `Assets → Refresh`를 실행합니다. Git LFS가 설치되어 있어야 하며, 저장소에 원본이 업로드되어 있어야 합니다.

```sh
git lfs install
git lfs pull
```

ZIP에는 `.git` 폴더가 없으므로 위 명령을 사용할 수 없습니다. 최신 ZIP을 다시 받거나 저장소를 clone하세요. 이미지가 정상 PNG인지 확인한 뒤에도 임포트 오류가 남으면 해당 에셋에 `Reimport`를 실행하고 Console 오류를 확인하세요.

## 수정본을 올릴 때

`.gitattributes` 변경뿐 아니라 PNG·TTF·PDF의 포인터 → 실제 파일 변경도 **함께 커밋하고 push**해야 합니다. 규칙만 올리면 이미 저장된 포인터가 원본으로 바뀌지 않습니다. 기존 커밋 기록은 변경하지 않습니다.

에셋을 공유할 때는 `.meta` 파일도 함께 커밋합니다. `Library`, `Temp`, `Logs`는 Unity가 다시 만드는 로컬 파일이므로 올리지 않습니다.
