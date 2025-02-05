# 📌 Inno Setup 설치 및 활용 방법

[Inno Setup 설치 및 활용 방법 블로그](https://naakjii.tistory.com/99)

---

## 🔹 1. Inno Setup 설치하기
### 🔹 설치 방법
1. [Inno Setup 공식 사이트](https://jrsoftware.org/isinfo.php)에서 다운로드  
2. 설치 후 `Inno Setup Compiler` 실행
   ![image](https://github.com/user-attachments/assets/790247ca-2c1c-45c9-8649-fe6f54c6f280)


---

## 🔹 2. 기본적인 Inno Setup 설정
### ✅ `Script Wizard`로 설치 파일 생성 (간단한 방법)
1. Inno Setup 실행 후 `File` → `New` → `Script Wizard`
![image](https://github.com/user-attachments/assets/88ed5f1e-6e0e-48eb-8755-7fe126bcc0a8)
![image](https://github.com/user-attachments/assets/8d558af3-66ee-404f-afa2-1bc8844f5b06)

2. 프로젝트 정보를 입력
![image](https://github.com/user-attachments/assets/b35b4bd2-ad45-47e1-a5a4-9fb38b9e7e11)

3. 프로그램 실행 파일 및 관련 파일 추가 (`*.exe`, `*.dll` 등)
![image](https://github.com/user-attachments/assets/6e2898c7-5ad2-493d-80d7-2491ae864b2a)

4. `Output` 디렉토리 설정 후 `Compile` 실행 → 설치 파일 생성!
- 출력되는 결과물을 어떤 파일 형식으로 저장할 것인지에 관한 것이라는 데, 모르겠음
![image](https://github.com/user-attachments/assets/77d32d14-2d49-4018-894d-3404461b743f)
![image](https://github.com/user-attachments/assets/7db4ebc6-aac8-4363-8800-c39aea409a31)

5. 설치 중 표시될 문서
- License file:
설치 중 사용자에게 표시될 **라이선스 파일(TXT, RTF 등)**을 지정합니다.
예: "사용자 동의" 창에 표시될 내용.
- Information file shown before installation:
설치 전에 표시될 정보 파일(예: README 파일).
- Information file shown after installation:
설치 완료 후 사용자에게 표시될 정보 파일(예: 사용 설명서).
![image](https://github.com/user-attachments/assets/6226ae9a-2961-42b1-8feb-9e876f532579)

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
