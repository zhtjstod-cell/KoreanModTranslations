# Korean Mod Translations

Starsector 한국어 패치용 유저 모드 번역 보조 패치입니다.

현재 **v0.1.0-alpha**입니다. 번역 누락, 어색한 문장, 일부 UI 미번역이 남아 있을 수 있습니다.

## 지원 모드

- Nexerelin
- Ashes of The Domain 계열
- Arma Armatura
- Ashes of The Domain - Dreams of Past

설치된 모드만 자동 감지해서 번역합니다. 예를 들어 Nexerelin만 있으면 Nexerelin만 번역되고, Nexerelin/Ashes of The Domain/Arma Armatura가 모두 있으면 세 모드 번역이 모두 적용됩니다.

## 설치 방법

1. 기본 Starsector 한국어 패치를 먼저 설치합니다.
2. 기본 한국어 패치에서 요구하는 Starsector API JAR 덮어쓰기를 먼저 완료합니다.
3. 사용할 원본 모드(Nexerelin, Ashes of The Domain, Arma Armatura 등)를 평소처럼 `mods` 폴더에 설치합니다.
4. Releases에서 `KoreanModTranslations-v0.1.0-alpha.zip`을 받습니다.
5. ZIP을 풀어 나온 `KoreanModTranslations` 폴더를 Starsector의 `mods` 폴더에 넣습니다.
6. `KoreanModTranslations\install_mod_translations.bat`를 실행합니다.
7. 게임 런처에서 `Korean Mod Translations`를 활성화합니다.

## Ashes of The Domain / Starsector API JAR

Ashes of The Domain을 사용하는 경우 기본 한국어 패치와 동일하게 Starsector API JAR 교체가 먼저 적용되어 있어야 합니다.

이 패치는 기본 한국어 패치를 대체하지 않습니다. 기본 한국어 패치와 API JAR 적용을 먼저 끝낸 뒤, 이 모드 번역 패치를 추가로 설치하면 됩니다.

## 삭제/원복

`KoreanModTranslations\uninstall_mod_translations.bat`를 실행하면 설치 시 백업한 원본 파일을 복구하고 `Korean Mod Translations`를 비활성화합니다.

원본 모드를 업데이트하거나 수동으로 파일을 덮어쓴 뒤에는 다시 설치하기 전에 언인스톨을 먼저 실행하는 것을 권장합니다.

## 주의

- 알파 버전입니다. 테스트 세이브에서 먼저 확인하는 것을 권장합니다.
- 원본 모드 버전이 바뀌면 일부 번역은 적용되지 않을 수 있습니다.
- 원본 모드 파일은 포함하지 않습니다. 원본 모드는 별도로 설치해야 합니다.

