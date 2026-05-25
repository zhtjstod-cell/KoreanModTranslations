# Korean Mod Translations v0.1.0-alpha

Starsector 한국어 패치용 유저 모드 번역 보조 패치입니다.

## 지원 모드

- Nexerelin
- Ashes of The Domain 계열
- Arma Armatura
- Ashes of The Domain - Dreams of Past

설치된 모드만 감지해 적용합니다. 하나만 설치되어 있으면 해당 모드만 번역되고, 여러 개가 있으면 설치된 모드들에 대해 번역이 적용됩니다.

## 설치

1. 기본 Starsector 한국어 패치를 먼저 설치하고, 기본 한글패치의 설치 BAT를 실행합니다.
   - 기본 한글패치: https://github.com/zhtjstod-cell/Starsector-KoreanPatch
   - Ashes of The Domain 등 일부 모드는 기본 한글패치 BAT가 자동 적용하는 Starsector API JAR 패치가 필요합니다.
2. 사용할 원본 모드(Nexerelin, Ashes of The Domain, Arma Armatura 등)를 `mods` 폴더에 설치합니다.
3. Starsector API JAR, `starsector-core` JAR, 또는 원본 모드 JAR을 덮어쓰는 다른 패치/모드가 있다면 적용합니다.
4. 다른 패치가 core/API JAR을 통째로 덮어썼다면 기본 한글패치 BAT를 다시 실행합니다.
5. 릴리즈 ZIP을 풀어 `KoreanModTranslations` 폴더를 Starsector `mods` 폴더에 넣습니다.
6. `KoreanModTranslations\install_mod_translations.bat`를 실행합니다.
7. 게임 런처에서 `Korean Mod Translations`를 활성화합니다.

Ashes of The Domain - Theory of Toolbox는 `0.98a\starfarer.api.jar`를 core API JAR 기준으로 요구합니다. KMT installer는 AoTD Theory가 설치되어 있고 두 API JAR이 서로 다르면 AoTD API JAR을 `starsector-core\starfarer.api.jar`에 먼저 동기화한 뒤, KMT JAR 번역 패치를 다시 적용합니다.

## 다른 core/JAR 패치와 같이 쓰는 법

이 번역 모드는 일부 `starsector-core` JAR 및 원본 모드 JAR 안의 표시 문자열도 패치합니다.

따라서 설치 순서는 다음을 권장합니다.

1. 바닐라 Starsector 준비
2. 원본 유저 모드 설치
3. Starsector API JAR 또는 core JAR을 덮어쓰는 다른 모드/패치 적용
4. 기본 한국어 패치 BAT 실행 또는 재실행
5. `KoreanModTranslations\install_mod_translations.bat`를 마지막에 실행

AoTD Theory의 `0.98a\starfarer.api.jar` 요구사항은 5단계에서 installer가 자동으로 보정합니다.

다른 패치가 이미 바꾼 문자열은 이 번역 모드가 억지로 덮지 않습니다. 설치기는 현재 파일에서 원문이 정확히 일치하는 항목만 패치하고, 일치하지 않는 항목은 건너뛰며 리포트에 기록합니다.

구분 기준:

- 다른 패치가 JAR 파일을 통째로 덮어쓰는 방식이면, 기본 한글패치의 core/API JAR 수정분도 같이 사라질 수 있습니다. 이 경우 다른 패치를 먼저 적용하고, 기본 한글패치 BAT를 다시 실행한 뒤, KMT installer를 마지막에 실행하세요.
- 다른 패치가 현재 JAR에 일부 문자열/클래스만 부분 패치하는 방식이면 순서 영향이 덜하지만, 그래도 KMT installer는 마지막에 실행하는 것을 권장합니다.
- 어떤 방식인지 모르겠다면 안전하게 `다른 core/JAR 패치 적용 -> 기본 한글패치 BAT 재실행 -> KMT installer 실행` 순서를 사용하세요.

다른 core/JAR 패치를 새로 추가하거나 업데이트했다면, 그 패치를 먼저 다시 적용하고 기본 한글패치 BAT를 다시 실행한 뒤 `install_mod_translations.bat`를 마지막에 다시 실행하세요.

`install_mod_translations.bat`는 시작할 때 core/API JAR 상태를 검사합니다.

- 완전 바닐라 core/API JAR가 감지되면 설치를 중단하고 기본 한글패치 BAT 실행을 안내합니다.
- AoTD Theory API JAR 불일치가 감지되면 `0.98a\starfarer.api.jar`를 core API JAR에 자동 동기화한 뒤 진행합니다.
- KMT가 알고 있는 패치 상태면 그대로 진행합니다.
- 알 수 없는 수정 JAR이면 경고와 `reports\preflight_report.json`을 남기고 진행합니다.
- KMT는 현재 파일에서 원문이 정확히 일치하는 항목만 패치하므로, 다른 패치가 바꾼 문자열은 건너뜁니다.

## 크래시 진단/자가 수리

게임이 크래시난 뒤에는 다음 파일을 실행할 수 있습니다.

```bat
KoreanModTranslations\diagnose_crash_and_repair.bat
```

기본 실행은 최신 `starsector.log`를 읽고 진단 리포트만 작성합니다. 실제 수리까지 적용하려면 명령 프롬프트에서 다음처럼 실행하세요.

```bat
KoreanModTranslations\diagnose_crash_and_repair.bat --execute
```

현재 자가 수리기는 프로젝트 진행 중 확인된 크래시 패턴을 처리합니다.

- `BootstrapMethodError` / `StringConcatException`
  - JAR class 문자열 결합 recipe의 `\x01` 개수 불일치 수리
- `AoTD Theory of Toolbox: Market Test Failed`
  - AoTD `0.98a\starfarer.api.jar`와 core API JAR 불일치 수리
- `NumberFormatException`
  - `rules.csv` options 필드의 잘못된 literal `\n` 수리
- `RuleException: unmatched quote`
  - `rules.csv` 구조 컬럼 복구
- `JSONException`, `Duplicate key`, `Error loading`
  - 안전하게 특정 파일을 확정할 수 없으면 진단만 수행

같은 크래시 서명이 반복되면, 해당 JAR class 패치를 blocklist에 넣고 문제 파일을 백업에서 복구한 뒤 나머지 패치만 다시 적용합니다.

자가 수리기가 installer를 다시 실행할 때는 repair mode를 사용합니다. 이 경우에도 완전 바닐라 core/API JAR는 중단하지만, 알 수 없는 수정 JAR는 경고 후 진행합니다.

## 삭제

`KoreanModTranslations\uninstall_mod_translations.bat`를 실행하면 설치 시 백업한 원본 파일을 복구하고 번역 모드를 비활성화합니다.

## 알파 버전 안내

- 번역 누락이나 어색한 문장이 남아 있을 수 있습니다.
- 원본 모드 버전이 달라지면 일부 문자열은 적용되지 않을 수 있습니다.
- 원본 모드 파일은 포함하지 않습니다. 원본 모드는 별도로 설치해야 합니다.
- CSV 줄바꿈이 필요한 `rules.csv`/설명문 필드는 설치 시 실제 줄바꿈으로 복원됩니다.


