# Korean Mod Translations v0.1.0-alpha

Starsector 한국어 패치용 유저 모드 번역 보조 패치입니다.

## 지원 모드

- Nexerelin
- Ashes of The Domain 계열
- Arma Armatura
- Ashes of The Domain - Dreams of Past

설치된 모드만 감지해 적용합니다. 하나만 설치되어 있으면 해당 모드만 번역되고, 여러 개가 있으면 설치된 모드들에 대해 번역이 적용됩니다.

## 설치

1. 기본 Starsector 한국어 패치를 먼저 설치합니다.
2. 기본 한국어 패치가 요구하는 Starsector API JAR 덮어쓰기를 먼저 완료합니다.
3. 사용할 원본 모드(Nexerelin, Ashes of The Domain, Arma Armatura 등)를 `mods` 폴더에 설치합니다.
4. 릴리즈 ZIP을 풀어 `KoreanModTranslations` 폴더를 Starsector `mods` 폴더에 넣습니다.
5. `KoreanModTranslations\install_mod_translations.bat`를 실행합니다.
6. 게임 런처에서 `Korean Mod Translations`를 활성화합니다.

Ashes of The Domain은 기본 한국어 패치와 마찬가지로 Starsector API JAR 교체가 먼저 적용되어 있어야 합니다. 이 패치는 기본 한국어 패치를 대체하지 않고, 그 위에서 지원 모드 번역을 추가 적용합니다.

## 삭제

`KoreanModTranslations\uninstall_mod_translations.bat`를 실행하면 설치 시 백업한 원본 파일을 복구하고 번역 모드를 비활성화합니다.

## 알파 버전 안내

- 번역 누락이나 어색한 문장이 남아 있을 수 있습니다.
- 원본 모드 버전이 달라지면 일부 문자열은 적용되지 않을 수 있습니다.
- 원본 모드 파일은 포함하지 않습니다. 원본 모드는 별도로 설치해야 합니다.

