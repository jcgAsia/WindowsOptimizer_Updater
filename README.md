# Windows System Optimizer

브라우저 활동 모니터링 기반 광고 자동화 프로그램

## 📋 주요 기능

- **브라우저 모니터링**: Chrome, Edge 실시간 URL 추적
- **도메인 매칭**: mapping.xml 기반 자동 광고 트리거
- **백그라운드 실행**: 사용자 경험 방해 없이 백그라운드 탭 오픈
- **빈도 제어**: 도메인별 최소 간격(분) 설정
- **자동 업데이트**: GitHub Releases 기반 Squirrel 업데이트
- **설정 동기화**: 서버에서 mapping.xml 자동 다운로드

## 🖥️ 시스템 요구사항

- **OS**: Windows 10/11
- **Framework**: .NET Framework 4.8 (Windows 내장)
- **브라우저**: Chrome, Edge
- **권한**: 관리자 권한 (설치 시)

## 📦 설치

### 자동 설치 (권장)
```bash
# Setup.exe 실행 (Squirrel 설치)
Setup.exe
```

### 수동 빌드
```powershell
# 1. 프로젝트 빌드
dotnet publish -c Release -r win-x64 --self-contained false

# 2. Squirrel 패키지 생성
.\build-release.ps1 -Version "1.1.7"
```

## 🗑️ 제거

1. **제어판**: `설정 > 앱 > Windows System Optimizer > 제거`
2. **직접 실행**: `uninstall.exe` 실행

## ⚙️ 설정 파일 (mapping.xml)

```xml
<mappings>
  <map>
    <trigger>naver.com</trigger>
    <target>https://example.com/ad/naver</target>
    <frequency>30</frequency>
  </map>
</mappings>
```

**필드 설명**
- `trigger`: 모니터링 대상 도메인
- `target`: 광고 URL
- `frequency`: 재실행 최소 간격(분)

## 🔄 자동 업데이트

- **서버**: https://jcgasia.github.io/WindowsOptimizer_Updater/
- **매핑 파일**: https://raw.githubusercontent.com/jcgAsia/WindowsOptimizer_Updater/main/mapping.xml
- **체크 주기**: 1분 (업데이트), 10분 (설정)

## 🔗 관련 저장소

- **Release 배포**: [WindowsOptimizer_Updater](https://github.com/jcgAsia/WindowsOptimizer_Updater)
- **Mapping 파일**: [mapping.xml](https://github.com/jcgAsia/WindowsOptimizer_Updater/blob/main/mapping.xml)

## 📁 디렉토리 구조

```
C:\Users\[User]\AppData\Local\WindowsOptimizer\
├── config\
│   └── mapping.xml (동기화된 매핑)
├── logs\
│   └── app_yyyyMMdd.log
└── app-[version]\
    └── WindowsOptimizer.exe
```

## 🛠️ 기술 스택

- **.NET Framework 4.8**
- **WPF + MVVM** (CommunityToolkit.Mvvm)
- **Squirrel** (자동 업데이트)
- **Costura.Fody** (단일 exe 패키징)
- **Windows Automation API** (브라우저 모니터링)

## 📝 라이선스

Proprietary - JCG

---

**버전**: 1.1.7  
**최종 업데이트**: 2025-12-02
