# 📌 Inno Setup 설치 및 활용 방법

[Inno Setup 설치 및 활용 방법 블로그](https://naakjii.tistory.com/99)

---

## 🔹 1. Inno Setup 설치하기
### 🔹 설치 방법
1. [Inno Setup 공식 사이트](https://jrsoftware.org/isinfo.php)에서 다운로드  
2. 설치 후 Inno Setup Compiler 실행  
   ![image](https://github.com/user-attachments/assets/790247ca-2c1c-45c9-8649-fe6f54c6f280)

---

## 🔹 2. 기본적인 Inno Setup 설정
### ✅ Script Wizard로 설치 파일 생성 (간단한 방법)
1. Inno Setup 실행 후 File → New → Script Wizard

### **옵션 설명**
- **Create a new empty script file**:  
  - 프로젝트 정보나 설정 없이 완전히 빈 상태로 스크립트를 작성할 때 사용.  
  - 스크립트를 처음부터 직접 작성해야 하므로 기본 설정이 없습니다.

- **Create a new script file using the Script Wizard**:  
  - Script Wizard를 통해 단계별로 프로젝트 정보를 입력하고 스크립트를 자동 생성.  
  - 기본적으로 이 옵션을 선택하는 것이 간편합니다.

- **Open an existing script file**:  
  - 이미 작성된 .iss 파일(예: AutoBridgeInstaller.iss)을 열어서 수정하거나 다시 컴파일.

   ![image](https://github.com/user-attachments/assets/88ed5f1e-6e0e-48eb-8755-7fe126bcc0a8)  
   ![image](https://github.com/user-attachments/assets/8d558af3-66ee-404f-afa2-1bc8844f5b06)

2. 프로젝트 정보를 입력  
   ![image](https://github.com/user-attachments/assets/b35b4bd2-ad45-47e1-a5a4-9fb38b9e7e11)

3. 설치 경로 지정  
   - **Application destination base folder**: 기본값은 Program Files 폴더 (C:\Program Files).  
   - 64비트 프로그램은 기본값 유지. 32비트 프로그램은 Custom을 선택하고 C:\Program Files (x86) 입력.  
   - **Application folder name**: 프로그램 폴더 이름 입력.  

   ![image](https://github.com/user-attachments/assets/24ebad54-fe55-485a-8d86-b9b087826168)

4. 프로그램 실행 파일 및 관련 파일 추가 (*.exe, *.dll 등)  
   - EXE 파일이 없으면 "The application doesn't have a main executable file" 옵션을 선택하세요.  
   ![image](https://github.com/user-attachments/assets/cf2167f6-1d76-4d72-902a-95e6339979f5)

5. Output 디렉토리 설정 후 Compile 실행 → 설치 파일 생성!  
   ![image](https://github.com/user-attachments/assets/77d32d14-2d49-4018-894d-3404461b743f)  
   ![image](https://github.com/user-attachments/assets/7db4ebc6-aac8-4363-8800-c39aea409a31)

6. 설치 중 표시될 문서 (선택사항)  
   - **License file**: 설치 중 사용자에게 표시될 **라이선스 파일(TXT, RTF 등)** 지정.  
     예: "사용자 동의" 창 내용.  
   - **Information file shown before installation**: 설치 전에 표시될 정보 파일(예: README 파일).  
   - **Information file shown after installation**: 설치 완료 후 표시될 정보 파일(예: 사용 설명서).  
   ![image](https://github.com/user-attachments/assets/6226ae9a-2961-42b1-8feb-9e876f532579)

7. 모든 사용자 계정에서 프로그램을 사용할 수 있도록 설치  
   ![image](https://github.com/user-attachments/assets/1e2f08a8-8014-441b-ae79-29ef3653fee9)

8. 레지스트리 특정하지 맙시다. Revit은 버전이 다양하기 때문입니다.  
   ![image](https://github.com/user-attachments/assets/19bc5a8b-9462-4d57-99b8-3417ccd2efbe)

9. 컴파일 설정  
   - **Custom compiler output folder**: 설치 파일(EXE)을 저장할 폴더를 지정.  
   - **Compiler output base file name**: 설치 파일 이름을 설정.  
     예: mysetup → 결과 파일은 mysetup.exe.  
   - **Custom Setup icon file**: 설치 파일(EXE)에 사용할 아이콘(.ico 파일) 지정.  
   - **Setup password**: 설치 파일에 암호를 설정하여, 설치 시 암호 입력 요구.  
   ![image](https://github.com/user-attachments/assets/ebd4db9c-1b1e-465d-904d-bd15667deb71)

10. 스크립트를 재사용할 건가요?  
   - **Inno Setup Preprocessor란?**  
     스크립트를 단순화하고 재사용 가능한 구조로 만들기 위한 기능입니다.  
     #define 지시문으로 변수와 상수를 정의하여 스크립트를 쉽게 변경 가능.  
   - **Yes, use #define compiler directives**: Preprocessor 기능 활성화.  
     ![image](https://github.com/user-attachments/assets/c044f280-f2d2-4db2-94b3-41d4deb1d756)

11. 액세스 거부 해결 방법  
   - **Inno Setup Compiler를 관리자 권한으로 실행**하세요.  
   - **출력 경로를 다른 폴더**로 변경. 예: C:\AutoBridgeDesign.  
     ![image](https://github.com/user-attachments/assets/16116e78-2f2a-413c-a0a5-463e08162a77)

---

## 🔹 3. 직접 Inno Setup 스크립트 작성하기
### ✅ 기본 setup.iss 예제
아래 코드를 setup.iss 파일로 저장한 후 Compile하면 EXE 설치 파일을 생성할 수 있습니다.

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

### ✅ 변수 활용
우리는 모든 Revit ver. 그리고 수십 개의 dll을 컴파일 해야합니다. [Files] 아래에 그 모든 것을 넣는다면 아래와 같이 가독성이 떨어질 것입니다. (심지어 2024버젼만 컴파일하는 예제입니다.)

```ini
[Files]
// ProgramData 경로 (공용 Addins 경로)

Source: "ControlzEx.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DBM.addin"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DevExpress.Data.v23.2.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DevExpress.Xpo.v23.2.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DnsClient.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DocumentFormat.OpenXml.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DocumentFormat.OpenXml.Framework.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "EPPlus.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "EPPlus.Interfaces.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "EPPlus.System.Drawing.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "ExcelDataReader.DataSet.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "ExcelDataReader.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Interop.ACTIVEXLib.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Interop.VSTOEE100.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MahApps.Metro.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MaterialDesignColors.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MaterialDesignThemes.Wpf.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Microsoft.Bcl.AsyncInterfaces.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Microsoft.Extensions.Logging.Abstractions.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Microsoft.Vbe.Interop.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Microsoft.Win32.Registry.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Microsoft.Xaml.Behaviors.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MongoDB.Bson.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MongoDB.Driver.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MongoDB.Driver.xml"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Newtonsoft.Json.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "PresentationCore.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "PresentationFramework.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "RevitAPI.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "RevitAPIUI.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "SharpCompress.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Snappier.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Buffers.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.ComponentModel.Annotations.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.ComponentModel.Composition.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.ComponentModel.DataAnnotations.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Configuration.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Data.DataSetExtensions.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Data.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Drawing.Common.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Drawing.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.IO.Compression.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.IO.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Memory.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Net.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Net.Http.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Numerics.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Numerics.Vectors.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Runtime.CompilerServices.VisualC.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Runtime.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Runtime.InteropServices.RuntimeInformation.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.AccessControl.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.Cryptography.Algorithms.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.Cryptography.Encoding.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.Cryptography.Primitives.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.Cryptography.X509Certificates.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.Principal.Windows.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Text.Encoding.CodePages.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Threading.Tasks.Extensions.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "WindowsBase.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "WindowsFormsIntegration.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "ZstdSharp.dll"; DestDir: "{commonappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion






// 사용자별 AppData 경로 (Roaming Addins 경로)
Source: "ControlzEx.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DBM.addin"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DevExpress.Data.v23.2.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DevExpress.Xpo.v23.2.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DnsClient.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DocumentFormat.OpenXml.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "DocumentFormat.OpenXml.Framework.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "EPPlus.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "EPPlus.Interfaces.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "EPPlus.System.Drawing.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "ExcelDataReader.DataSet.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "ExcelDataReader.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Interop.ACTIVEXLib.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Interop.VSTOEE100.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MahApps.Metro.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MaterialDesignColors.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MaterialDesignThemes.Wpf.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Microsoft.Bcl.AsyncInterfaces.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Microsoft.Extensions.Logging.Abstractions.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Microsoft.Vbe.Interop.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Microsoft.Win32.Registry.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Microsoft.Xaml.Behaviors.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MongoDB.Bson.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MongoDB.Driver.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "MongoDB.Driver.xml"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Newtonsoft.Json.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "PresentationCore.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "PresentationFramework.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "RevitAPI.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "RevitAPIUI.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "SharpCompress.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "Snappier.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Buffers.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.ComponentModel.Annotations.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.ComponentModel.Composition.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.ComponentModel.DataAnnotations.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Configuration.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Data.DataSetExtensions.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Data.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Drawing.Common.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Drawing.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.IO.Compression.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.IO.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Memory.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Net.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Net.Http.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Numerics.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Numerics.Vectors.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Runtime.CompilerServices.VisualC.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Runtime.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Runtime.InteropServices.RuntimeInformation.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.AccessControl.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.Cryptography.Algorithms.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.Cryptography.Encoding.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.Cryptography.Primitives.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.Cryptography.X509Certificates.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Security.Principal.Windows.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Text.Encoding.CodePages.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "System.Threading.Tasks.Extensions.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "WindowsBase.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "WindowsFormsIntegration.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion
Source: "ZstdSharp.dll"; DestDir: "{userappdata}\Autodesk\Revit\Addins\2024"; Flags: ignoreversion



// ProgramData 경로 (공용 Addins 경로)
Source: "System.Runtime.dll"; DestDir: "C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\.NETFramework\v4.8\Facades"; Flags: ignoreversion
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
- {commonpf} (C:\Program Files\Common Files) 같은 경로를 사용.  
- setup.iss에서 **경로 변경**.  

ini
[Setup]
DefaultDirName={commonpf}\내프로그램


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
3. **직접 setup.iss를 작성하여 EXE 패키징.**  
4. **한글 & 공백 문제 해결 후 컴파일 진행.**  

---
