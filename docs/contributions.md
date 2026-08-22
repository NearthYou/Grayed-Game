# 팀 결과와 개인 기여

Grayed Game은 기획, 개발, 아트와 사운드가 함께 만든 팀 프로젝트입니다. 전시와 수상, 전체 게임 설계와 asset은 개인 성과로 표시하지 않습니다.

## 팀 결과

- 2024 BIC Rookie 부문 on-site와 online exhibition
- 2024 LOGIN 대학생 연합 발표회 기획 우수상
- 챕터별 장르와 시스템을 결합한 실행 가능한 build

## 이시원 참여 범위

| 항목 | 내용 |
| --- | --- |
| 참여 기간 | 2024.10 - 2026.01 |
| 협업 형태 | 프로그래머 2명과 기획, 아트, 사운드 직군 협업 |
| 주요 범위 | CH3 grid, editor tool, 건설과 생산, teleporter, Dancepace, dialogue와 interaction |

## source와 Git history에서 확인되는 작업

| 영역 | 대표 작업 | 근거 |
| --- | --- | --- |
| CH3 base | 플레이어 movement, grid, minimap, 자원과 object interaction | 2025-02부터 2025-08까지 CH3 commit |
| Dancepace | data, wave, input timing, character, UI와 sound presentation | 2025-06부터 2026-01까지 Dancepace commit |
| Tile editor | placement, spawn point, block fill, 좌표와 겹침 fix | `31d47943`, `1a2a4924`, `e7c62cdf`, `48d4956e` |
| Building | build mode, factory, 생산, crafting과 inventory | `32fe71d0`, `c7be4f3d`, `ae5598d7`, `543518cb` |
| Teleporter | region activation, list UI, fade와 distance close | `acf35fde`, `673d5357` |
| 유지보수 | reflection 제거, memory risk 정리, editor build 제외 | `d1d2a407`, `220c1d84`, `58dcede5` |

commit은 작업 범위를 찾는 근거입니다. merge 뒤 다른 programmer와 직군이 수정한 결과까지 개인 단독 구현으로 넓혀 쓰지 않습니다.

## 대표 문제

기획자의 맵 수정이 프로그래머 재배치와 build를 거치던 흐름을 Unity EditorWindow로 바꿨습니다. 기획자는 scene 안에서 object를 편집하고 Play로 결과를 바로 확인할 수 있게 됐습니다.

Editor 성능은 같은 scene에서 1084.8ms에서 52.7ms로 줄어든 프로젝트 기록이 있습니다. 원본 profiler distribution을 보존하지 못했으므로 반복 가능한 benchmark나 평균 개선율로 표시하지 않습니다.

## 범위 밖

- 팀 전체의 게임 설계와 story ownership
- 아트, 음악과 사운드 asset 제작
- BIC exhibition과 LOGIN award의 개인 귀속
- 다른 프로그래머의 chapter와 시스템 구현
- 원본 profiler log가 없는 성능 일반화
