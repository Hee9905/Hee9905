c# 개발 환경 설정 방법 (console, wpf, usercontrollib 등 모든 형태의 프로젝트 개발)
====================================================

# vscode 사용

## 개발 환경 구축
### vscode extension
* C# 사용
  * C# Dev Kit (C# 데브킷)은 미사용 (라이선스 필요)
* .NET Extension Pack 사용 (MIT License)

  
### .NET SDK 사용
  * Visual Studio 2022용 빌드 도구 다운로드
  * Link : [Visual Studio Tools 다운로드](https://visualstudio.microsoft.com/ko/downloads/) - 하단에 모든다운로드에서 Visual Studio 도구 클릭
  * visual studio installer 에 visual studio build tools 2022 에서 '.NET 데스크톱 빌드 도구' 선택 후 '.NET SDK' 설치


## vscode setting
vscode setting(ctrl + ,)에 들어가서 Omnisharp 검색, Use Omnisharp 체크 (default 는 미체크)
* OmniSharp는 .NET 개발자들을 위한 오픈 소스 프로젝트로, 다양한 코드 편집기와 IDE에서 C# 개발 환경을 제공하는 도구
* Omnisharp을 사용하여 C# Dev Kit 기능 수행
* C# extension에 들어있는 옵션
* 사용으로 변경하면 자동으로 Omnisharp 설치 수행

## 프로젝트 생성, 빌드 및 실행
  1. vscode의 터미널 사용 또는 "Developer Command Prompt for VS 2022" 사용
      * Developer Command Prompt for VS 2022는 visual studio build tools 2022 설치시 자동 설치
      * 시작에서 Developer Command Prompt for VS 2022 검색 
  2. 프로젝트 폴더 생성
  3. 
```bash
dotnet new console -n ConsoleTest
dotnet new wpf -n WpfTest
dotnet new wpfusercontrollib -n UserControlTest
...
     
cd UserControlTest
dotnet build
dotnet run
```


## 디버깅
  1. launch.json 생성
     * 디버깅 메뉴 (ctrl+shift+D)
     * "create a launch.json file" 실행
     * ".NET Core" 선택
  2. launch.json 작성
     * 우측하단에 파랑색 'Add Configuration' 클릭
     * 스크롤을 올려서 '{} .NET: Attach to a .Net process' , '{} .NET: Launch Executable file (Console)' 클릭
     * launch.json 샘플
     ```json
     {
        "version": "0.2.0",
        "configurations": [
            {
                "name": ".NET Core Launch (console)",
                "type": "coreclr",
                "request": "launch",
                "preLaunchTask": "build",
                "program": "${workspaceFolder}/bin/Debug/net8.0-windows/WpfTest.dll",
                "args": [],
                "cwd": "${workspaceFolder}",
                "console": "internalConsole",
                "stopAtEntry": false
            },
            {
                "name": ".NET Core Attach",
                "type": "coreclr",
                "request": "attach"
            }
        ]
     }
 
  3. F5로 디버깅 시작
