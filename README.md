# Korean Mod Translations v0.1.1-alpha

Starsector 한국어 패치용 유저 모드 번역 보조 패치입니다.

현재 알파 버전입니다. 번역 누락, 어색한 문장, 일부 UI 미번역이 남아 있을 수 있습니다.

## 지원 모드

- Nexerelin
- Ashes of The Domain 계열
- Arma Armatura
- Ashes of The Domain - Dreams of Past
- MagicLib 현상금/위치 문구 일부

설치된 모드만 자동으로 감지해서 번역합니다. 예를 들어 Nexerelin만 있으면 Nexerelin 관련 번역만 적용되고, 여러 모드가 있으면 설치된 모드 번역이 함께 적용됩니다.

## 설치

1. 기본 Starsector 한국어 패치를 먼저 설치하고 기본 한글패치의 설치 BAT를 실행합니다.
   - 기본 한글패치: https://github.com/zhtjstod-cell/Starsector-KoreanPatch
2. Nexerelin, Ashes of The Domain, Arma Armatura 등 사용할 원본 모드를 평소처럼 `mods` 폴더에 설치합니다.
3. Starsector API JAR, `starsector-core` JAR, 또는 원본 모드 JAR을 덮어쓰는 다른 패치/모드가 있다면 적용합니다.
4. 다른 패치가 core/API JAR을 통째로 덮어썼다면 기본 한글패치 BAT를 다시 실행합니다.
5. 이 폴더 `KoreanModTranslations`를 Starsector의 `mods` 폴더에 넣습니다.
6. `install_mod_translations.bat`를 실행합니다.
7. 게임 런처에서 `Korean Mod Translations`를 활성화합니다.

## 다른 Core/JAR 패치와 같이 쓰는 법

이 번역 모드는 일부 `starsector-core` JAR 및 원본 모드 JAR 안의 표시 문자열도 패치합니다.

권장 순서:

1. 바닐라 Starsector 준비
2. 기본 한국어 패치 설치 BAT 실행
3. 원본 유저 모드 설치
4. Starsector API JAR 또는 core JAR을 덮어쓰는 다른 모드/패치 적용
5. 다른 패치가 core/API JAR을 덮어썼다면 기본 한국어 패치 BAT 재실행
6. `KoreanModTranslations\install_mod_translations.bat` 실행

AoTD Theory의 `0.98a\starfarer.api.jar` 요구사항은 installer가 자동으로 보정합니다.

이번 빌드는 core/AoTD API JAR의 개인 현상금 및 루드의 길 술집 이벤트 하드코딩 문구, Arma Armatura의 `armaa.jar` 하드코딩 문구, MagicLib 현상금 위치 문구를 추가로 보정합니다.

## 삭제/원복

`uninstall_mod_translations.bat`를 실행하면 설치 시 백업해 둔 원본 파일을 복구하고 `Korean Mod Translations`를 비활성화합니다.

원본 모드 파일은 처음 패치하기 전에 백업됩니다. 원본 모드를 업데이트하거나 수동으로 파일을 덮어쓴 뒤에는 다시 설치하기 전에 언인스톨을 먼저 실행하는 것을 권장합니다.

## 크래시 진단/자가 수리

게임이 크래시난 뒤 `diagnose_crash_and_repair.bat`를 실행하면 최신 `starsector.log`를 읽고 알려진 크래시 패턴을 진단합니다.

기본 실행은 리포트만 작성합니다. 실제 수리를 적용하려면 명령 프롬프트에서 다음처럼 실행하세요.

```bat
diagnose_crash_and_repair.bat --execute
```

현재 자동 수리 룰은 다음을 다룹니다.

- Java `StringConcatException` / `BootstrapMethodError`
- `AoTD Theory of Toolbox: Market Test Failed`
- `Duplicate key ... rules.csv`
- `NumberFormatException`
- `RuleException: unmatched quote`

## 주의

- 알파 버전이므로 새 세이브보다 테스트 세이브에서 먼저 확인하는 것을 권장합니다.
- 원본 모드 버전이 바뀌면 일부 번역은 적용되지 않을 수 있습니다.
- 번역 패치는 원본 모드를 포함하지 않습니다. 각 원본 모드는 따로 설치해야 합니다.
## AoTD 활성화 진단

AoTD 콘텐츠가 일부 바닐라처럼 보이거나 `D` 키 연구 탭이 제대로 나오지 않으면 다음 파일을 실행하세요.

```bat
KoreanModTranslations\audit_aotd_activation.bat
```

이 진단은 AoTD 5개 모듈, 필수 의존성, AoTD Theory API 병합 상태, 최신 로그의 연구 매니저 로드 흔적을 확인하고 `reports\aotd_activation_audit.json` 및 `reports\aotd_activation_audit_ko.md`를 생성합니다.
