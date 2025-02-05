# 📌 Inno Setup 설치 및 활용 방법

[Inno Setup 설치 및 활용 방법 블로그](https://naakjii.tistory.com/99)

---

## 🔹 1. Inno Setup 설치하기
### 🔹 설치 방법
1. [Inno Setup 공식 사이트](https://jrsoftware.org/isinfo.php)에서 다운로드  
2. 설치 후 `Inno Setup Compiler` 실행  

---

## 🔹 2. 기본적인 Inno Setup 설정
### ✅ `Script Wizard`로 설치 파일 생성 (간단한 방법)
1. Inno Setup 실행 후 `File` → `New` → `Script Wizard`
2. 프로젝트 정보를 입력
3. 프로그램 실행 파일 및 관련 파일 추가 (`*.exe`, `*.dll` 등)
4. `Output` 디렉토리 설정 후 `Compile` 실행 → 설치 파일 생성!

---

## 🔹 3. 직접 Inno Setup 스크립트 작성하기
### ✅ 기본 `setup.iss` 예제
아래 코드를 `setup.iss` 파일로 저장한 후 `Compile`하면 EXE 설치 파일을 생성할 수 있습니다.

```ini
[Setup]
AppName=내 프로그램
AppVersion=1.0
DefaultDirName={pf}\내 프로그램
DefaultGroupName=내 프로그램
OutputDir=.
OutputBaseFilename=내프로그램설치파일
Compression=lzma
SolidCompression=yes

[Files]
Source: "C:\내프로그램\*"; DestDir: "{app}"; Flags: ignoreversion recursesubdirs

[Icons]
Name: "{group}\내 프로그램 실행"; Filename: "{app}\내프로그램.exe"

[Run]
Filename: "{app}\내프로그램.exe"; Description: "프로그램 실행"; Flags: nowait postinstall skipifsilent
```

---

## 🔹 4. 설치 중 오류 해결
### 🚨 사용자명에 한글 또는 공백이 포함된 경우
#### ✅ 해결 방법
✔ **A안) 사용자명과 관련 없는 경로에 설치**  
- `{commonpf}` (`C:\Program Files\Common Files`) 같은 경로를 사용
- `setup.iss`에서 **경로 변경**
  
```ini
[Setup]
DefaultDirName={commonpf}\내프로그램
```

✔ **B안) 사용자명 변경**  
- 사용자명을 바꾸는 방법: [네이버 블로그 참고](https://blog.naver.com/rkdalstj7504/222173490548)

---

## 🔹 5. 추가 참고 자료
- [Inno Setup 공식 문서](https://jrsoftware.org/ishelp/index.php)
- [Inno Setup 확장 플러그인 (ISPP)](https://jrsoftware.org/ispphelp/index.php)
- [Windows 사용자명 변경 방법](https://blog.naver.com/rkdalstj7504/222173490548)

---

## 📌 정리
1. **Inno Setup을 설치하고** 실행  
2. **Script Wizard를 활용해 간단히 설치 파일 생성**  
3. **직접 `setup.iss`를 작성하여 EXE 패키징**  
4. **한글 & 공백 문제 해결 후 컴파일 진행**  

---
