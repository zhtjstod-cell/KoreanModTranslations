# Korean Mod Translations v0.1.0-alpha

Starsector 한국어 패치용 유저 모드 번역 보조 패치입니다.

현재 알파 버전입니다. 번역 누락, 어색한 문장, 일부 UI 미번역이 남아 있을 수 있습니다.

## 지원 모드

- Nexerelin
- Ashes of The Domain 계열
- Arma Armatura
- Ashes of The Domain - Dreams of Past

설치된 모드만 자동으로 감지해서 번역합니다. 예를 들어 Nexerelin만 있으면 Nexerelin 관련 번역만 적용되고, 세 모드가 모두 있으면 세 모드 번역이 모두 적용됩니다.

## 기본 한국어 패치와 같이 쓰는 법

1. 기본 Starsector 한국어 패치를 먼저 설치하고, 기본 한글패치의 설치 BAT를 실행합니다.
   - 기본 한글패치: https://github.com/zhtjstod-cell/Starsector-KoreanPatch
   - Ashes of The Domain 등 일부 모드는 기본 한글패치 BAT가 자동 적용하는 Starsector API JAR 패치가 필요합니다.
2. Nexerelin, Ashes of The Domain, Arma Armatura 등 사용할 원본 모드를 평소처럼 `mods` 폴더에 설치합니다.
3. 이 폴더 `KoreanModTranslations`를 Starsector의 `mods` 폴더에 넣습니다.
4. `kmt_manager.bat`를 실행하고 `자동 설치/보정`을 누릅니다.
5. 게임 런처에서 `Korean Mod Translations`를 활성화합니다.

기존 방식이 필요하면 `install_mod_translations.bat`를 직접 실행해도 됩니다. 다만 일반 배포판에서는 `kmt_manager.bat` 사용을 권장합니다.

## KMT Manager

`kmt_manager.bat`는 별도 설치 없이 실행되는 간단한 GUI 매니저입니다.

- 현재 Starsector 폴더와 감지된 모드 수를 표시합니다.
- core/API JAR이 바닐라인지, 수정된 상태인지 검사합니다.
- AoTD Theory의 `0.98a\starfarer.api.jar` 요구사항을 자동 보정합니다.
- 지원 모드 번역 설치, 크래시 진단, 크래시 수리, 원복을 버튼으로 실행합니다.
- 작업 결과와 리포트 위치를 화면에서 확인할 수 있습니다.

Ashes of The Domain - Theory of Toolbox를 사용하는 경우, 설치기가 `0.98a\starfarer.api.jar`와 `starsector-core\starfarer.api.jar` 상태를 비교합니다. 서로 다르면 AoTD가 요구하는 API JAR을 core 쪽에 먼저 맞춘 뒤, 그 위에 KMT JAR 번역 패치를 다시 적용합니다.

다른 모드나 패치가 `starsector-core`의 JAR 파일을 수정한다면, 그 패치들을 먼저 적용한 뒤 이 모드의 설치 BAT를 마지막에 실행하세요. 설치기는 현재 JAR을 기준으로 원문이 정확히 일치하는 문자열만 추가 패치하고, 일치하지 않는 항목은 건너뜁니다.

설치기는 시작할 때 core/API JAR 상태를 검사합니다. AoTD Theory API JAR 불일치는 자동 보정하고, 완전 바닐라 JAR가 감지되면 기본 한글패치 BAT를 먼저 실행하라고 중단합니다. 이미 수정된 JAR는 경고/리포트만 남기고 진행하며, 현재 파일에 정확히 맞는 문자열만 패치합니다.

## 삭제/원복

`uninstall_mod_translations.bat`를 실행하면 설치 시 백업해 둔 원본 파일을 복구하고 `Korean Mod Translations`를 비활성화합니다.

원본 모드 파일은 처음 패치하기 전에 백업됩니다. 단, 원본 모드를 업데이트하거나 수동으로 파일을 덮어쓴 뒤에는 다시 설치하기 전에 언인스톨을 먼저 실행하는 것을 권장합니다.

## 크래시 진단/자가 수리

게임이 크래시난 뒤 `diagnose_crash_and_repair.bat`를 실행하면 최신 `starsector.log`를 읽고 알려진 크래시 패턴을 진단합니다.

GUI를 쓰는 경우 `kmt_manager.bat`에서 `크래시 진단` 또는 `크래시 수리 실행` 버튼을 누르면 됩니다.

기본 실행은 리포트만 작성합니다. 실제 수리를 적용하려면 명령 프롬프트에서 다음처럼 실행하세요.

```bat
diagnose_crash_and_repair.bat --execute
```

현재 자동 수리 룰은 다음을 다룹니다.

- Java `StringConcatException` / `BootstrapMethodError`: JAR 문자열 결합 recipe의 `\x01` 개수 불일치 수리
- `AoTD Theory of Toolbox: Market Test Failed`: AoTD `0.98a\starfarer.api.jar`를 core API JAR 기준으로 동기화한 뒤 설치기 재실행
- `NumberFormatException`: `rules.csv` options 필드의 잘못된 literal `\n` 수리
- `RuleException: unmatched quote`: `rules.csv` 구조 컬럼 복구

같은 크래시 서명이 반복되면 해당 JAR class 패치를 blocklist에 넣고, 백업 복구 후 나머지 패치만 다시 적용합니다.

자가 수리기가 installer를 다시 실행할 때는 repair mode로 실행되어 일반 설치보다 관대하게 동작하지만, 완전 바닐라 core/API JAR는 여전히 중단합니다.

## 주의

- 알파 버전이므로 새 세이브보다 테스트 세이브에서 먼저 확인하는 것을 권장합니다.
- 원본 모드 버전이 바뀌면 일부 번역은 적용되지 않을 수 있습니다.
- 번역 패치는 원본 모드를 포함하지 않습니다. 각 원본 모드는 따로 설치해야 합니다.


