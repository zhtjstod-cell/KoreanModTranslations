# Korean Mod Translations v0.1.2-alpha

Starsector 한국어 패치용 유저 모드 번역 보조 패치입니다.

이번 릴리스는 설치 BAT의 Python 실행 문제를 고친 핫픽스입니다.

## 핵심 변경

- `install_mod_translations.bat`, `uninstall_mod_translations.bat`, 진단 BAT가 `python` 명령에만 의존하지 않도록 수정했습니다.
- BAT 실행 시 Windows Python Launcher인 `py -3`을 먼저 사용하고, 없을 때만 실제 Python 3 `python` 명령을 검증해서 사용합니다.
- `python --version`이 버전 없이 `Python`만 출력되는 Windows Store alias/PATH 문제 환경에서도 설치가 막히지 않도록 했습니다.
- 기존 `v0.1.1-alpha`의 AoTD/AshLib 커맨드 탭 호환성 보정과 진단 도구는 유지됩니다.

## 설치 순서

1. 기본 Starsector 한국어 패치를 먼저 설치하고 기본 패치 BAT를 실행합니다.
   - https://github.com/zhtjstod-cell/Starsector-KoreanPatch
2. Nexerelin, Ashes of The Domain, Arma Armatura 등 원본 유저 모드를 `mods` 폴더에 설치합니다.
3. Starsector API JAR, `starsector-core` JAR, 원본 모드 JAR에 영향을 주는 다른 패치/모드가 있다면 먼저 적용합니다.
4. 다른 패치가 core/API JAR에 손댔다면 기본 한국어 패치 BAT를 다시 실행합니다.
5. 릴리즈 ZIP 안의 `KoreanModTranslations` 폴더를 Starsector `mods` 폴더에 넣습니다.
6. `KoreanModTranslations\install_mod_translations.bat`를 실행합니다.
7. 게임 런처에서 `Korean Mod Translations`를 활성화합니다.

## 주의

- 알파 버전입니다.
- 원본 모드 버전이 달라지면 일부 패치가 적용되지 않을 수 있습니다.
- 원본 모드 파일은 포함하지 않습니다. 각 원본 모드는 별도로 설치해야 합니다.
