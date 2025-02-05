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

### **옵션 설명**
- **Create a new empty script file**: 빈 상태로 스크립트 작성.
- **Create a new script file using the Script Wizard**: 프로젝트 정보를 입력하고 자동 생성.
- **Open an existing script file**: 기존 `.iss` 파일을 열어 수정.

2. 프로젝트 정보 입력
3. 설치 경로 지정
4. 프로그램 실행 파일 및 관련 파일 추가 (`*.exe`, `*.dll` 등)
5. `Output` 디렉토리 설정 후 `Compile` 실행 → 설치 파일 생성!

---

## 🔹 3. 직접 Inno Setup 스크립트 작성하기
### ✅ 기본 `setup.iss` 예제

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

## 🔹 4. 컴파일해야 하는 파일의 기준

### 📌 확인해야 할 사항
- **프로젝트의 빌드 출력 (Build Output)**
  - Visual Studio에서 `bin\Release` 또는 `bin\Debug` 폴더 확인.
  - 핵심 라이브러리 (`AutoBridgeDesign.dll` 등) 포함 여부 체크.

- **프로젝트 참조 외부 라이브러리**
  - NuGet 패키지 또는 추가한 외부 DLL (`DevExpress`, `EPPlus`, `Newtonsoft.Json`, `RevitAPI.dll` 등).

- **Revit Add-In 파일**
  - `.addin` 파일: Add-In 등록 필수.
  - `.dll` 파일: Revit API 활용 라이브러리 포함.

- **설치 대상 폴더**
  - `{commonappdata}\Autodesk\Revit\Addins\2024` 폴더 사용.
  - `2018~2026` 버전 지원하려면 `{commonappdata}\Autodesk\Revit\Addins\XXXX` 구조 적용.

### 📌 VS에서 확인할 방법
1. Visual Studio 열기
2. 솔루션 탐색기 → `bin\Release` 또는 `bin\Debug` 폴더 열기
3. `.dll`, `.exe`, `.addin` 파일 확인 후 정리
4. `filelist_programdata.txt` & `filelist_appdata.txt` 파일 생성 후 Inno Setup에서 활용 🔥

---

## 🔹 5. 설치 중 오류 해결

### 🚨 사용자명에 한글 또는 공백이 포함된 경우
#### ✅ 해결 방법
✔ **A안) 사용자명과 관련 없는 경로에 설치**
```ini
[Setup]
DefaultDirName={commonpf}\내프로그램
```
✔ **B안) 사용자명 변경**  
- 사용자명을 바꾸는 방법: [네이버 블로그 참고](https://blog.naver.com/rkdalstj7504/222173490548)

---

## 🔹 6. 추가 참고 자료
- [Inno Setup 공식 문서](https://jrsoftware.org/ishelp/index.php)
- [Inno Setup 확장 플러그인 (ISPP)](https://jrsoftware.org/ispphelp/index.php)
- [Windows 사용자명 변경 방법](https://blog.naver.com/rkdalstj7504/222173490548)

---

## 📌 정리
1. **Inno Setup을 설치하고** 실행.
2. **Script Wizard를 활용해 간단히 설치 파일 생성.**
3. **직접 `setup.iss`를 작성하여 EXE 패키징.**
4. **한글 & 공백 문제 해결 후 컴파일 진행.**
