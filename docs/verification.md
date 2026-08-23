# 검증 기록

## 현재 프로젝트 기준

| 항목 | 확인 결과 |
| --- | --- |
| Unity | 2022.3.62f2, revision `7670c08855a9` |
| 개발 기간 | 2023.09 - 2026.01 프로젝트 기록 |
| 공개 영상 | [YouTube play video](https://www.youtube.com/watch?v=fdvunwIGKAs) |
| 공개 build | README의 Google Drive link |
| 팀 결과 | 2024 BIC Rookie 전시, 2024 LOGIN 기획 우수상 |

팀 결과는 현재 README의 프로젝트 기록을 유지합니다. 이 작업에서는 행사 사이트나 수상 증서를 새로 수집하지 않았습니다.

## source 대조

다음 설명은 현재 source에서 확인했습니다.

- `GridTileEditor`의 direct GridSystem reference, no forced Repaint와 occupied position HashSet
- `CH3_LevelData`, `GridSystem`과 `BuildingObjectFactory`의 shared object rule
- BaseCamp가 처음부터 active인 teleporter state
- BaseCamp, Michael, Farmer, Dollar region order
- 2m interaction range와 0.1초 teleport delay
- interaction range 밖에서 닫히는 TeleportUI
- Dancepace의 ScriptableObject, enum, string table과 flow class

## Editor frame time

README에는 같은 장비와 같은 scene에서 Editor main thread frame time이 1084.8ms에서 52.7ms로 줄었다는 기록이 있습니다.

raw profiler log, 반복 횟수와 frame time distribution은 저장소에 없습니다. 따라서 이 값은 당시 same-scene observation으로만 남기고 p95, 평균 개선율이나 다른 PC의 결과로 바꾸지 않습니다.

## 문서 정리 검증

- GameOver 가제와 미완성 chapter placeholder는 현재 설계에서 제거
- 2024 meeting, interview, recruitment와 temporary plan 삭제
- 외부 core mechanic PDF 보존
- package README와 license 무변경
- source, scene와 asset 무변경
- 내부 link와 image path 확인
- `git diff --check` 실행

## 자동화 범위

현재 확인한 source에는 Unity Test Framework test assembly가 없습니다. `Assets/Scripts/Editor/Scripts.Editor.asmdef`는 editor assembly이며 test assembly가 아닙니다.

이 문서 개편은 source 확인, 프로젝트 version, Git history, local link와 Markdown diff로 검증합니다. gameplay와 editor 성능을 새로 실행했다고 주장하지 않습니다.
