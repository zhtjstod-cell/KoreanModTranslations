# Korean Mod Translations v0.1.1-alpha

Starsector 한국어 패치용 유저 모드 번역 보조 패치입니다.

## 핵심 변경

- AoTD Vaults of Knowledge 연구/생산 탭이 열리지 않던 문제를 수정했습니다.
- AoTD/Ashlib 커맨드 탭 삽입 로직이 바닐라 영문 탭명을 기준으로 동작하는 점을 반영해, 커맨드 화면 핵심 탭명 5개를 영문으로 유지하도록 보정했습니다.
  - Colonies
  - Orders
  - Income
  - Doctrine & blueprints
  - Custom production
- 잘못된 Ashlib 공통 탭 추적기 패치는 제거했습니다. 이 패치는 `CommandTabTracker.insertButton()` NPE를 유발할 수 있어 배포 대상에서 제외했습니다.
- AoTD 5개 모듈 활성화/호환성 감사 도구를 추가했습니다.
  - `audit_aotd_activation.bat`
  - `audit_aotd_activation.py`
- AoTD Theory API 병합 로직을 유지합니다. KoreanPatch가 적용된 core API 문자열을 보존하면서 AoTD Theory의 변경 클래스가 반영되도록 처리합니다.

## 지원 모드

- Nexerelin
- Ashes of The Domain 계열
  - Theory of Toolbox
  - Vaults of Knowledge
  - Seats of Power
  - Question of Loyalty
  - Dreams of Past
- Arma Armatura
- MagicLib 일부 현상금/위치 문구

설치된 모드만 자동 감지해 번역/보정합니다. 원본 유저 모드는 포함하지 않습니다.

## 설치 순서

1. 기본 Starsector 한국어 패치를 먼저 설치하고 기본 패치 BAT를 실행합니다.
   - https://github.com/zhtjstod-cell/Starsector-KoreanPatch
2. Nexerelin, Ashes of The Domain, Arma Armatura 등 원본 유저 모드를 `mods` 폴더에 설치합니다.
3. Starsector API JAR, `starsector-core` JAR, 원본 모드 JAR에 영향을 주는 다른 패치/모드가 있다면 먼저 적용합니다.
4. 다른 패치가 core/API JAR에 손댔다면 기본 한국어 패치 BAT를 다시 실행합니다.
5. 릴리즈 ZIP 안의 `KoreanModTranslations` 폴더를 Starsector `mods` 폴더에 넣습니다.
6. `KoreanModTranslations\install_mod_translations.bat`를 실행합니다.
7. 게임 런처에서 `Korean Mod Translations`를 활성화합니다.

## AoTD 탭 호환성 참고

AoTD/Ashlib의 커맨드 탭 확장 코드는 일부 바닐라 탭명을 표시 문자열로 검색합니다. 이 문자열을 한국어로 바꾸면 AoTD 연구/생산 탭이 삽입되지 않거나 크래시가 날 수 있습니다.

이번 버전은 기능 보존을 우선해 커맨드 화면 상단의 일부 바닐라 탭명을 영문으로 유지합니다. 게임 내 다른 번역은 가능한 범위에서 유지됩니다.

## 진단

AoTD 컨텐츠가 덜 활성화된 것처럼 보이면 다음을 실행해 상태를 확인할 수 있습니다.

```bat
KoreanModTranslations\audit_aotd_activation.bat
```

크래시 후에는 다음을 실행해 알려진 크래시 패턴을 진단할 수 있습니다.

```bat
KoreanModTranslations\diagnose_crash_and_repair.bat
```

실제 자동 복구까지 적용하려면 명령 프롬프트에서 다음처럼 실행합니다.

```bat
KoreanModTranslations\diagnose_crash_and_repair.bat --execute
```

## 주의

- 알파 버전입니다. 번역 누락, 어색한 문장, 일부 UI 미번역이 남아 있을 수 있습니다.
- 원본 모드 버전이 달라지면 일부 패치가 적용되지 않을 수 있습니다.
- 원본 모드 파일은 포함하지 않습니다. 각 원본 모드는 별도로 설치해야 합니다.
