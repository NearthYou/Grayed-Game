# 구현 역할

Grayed Game은 기획, 개발, 아트와 사운드가 함께 만든 팀 프로젝트입니다. 2024 BIC Rookie 전시와 2024 LOGIN 기획 우수상을 받았습니다.

## 이시원

| 항목 | 내용 |
| --- | --- |
| 참여 기간 | 2024.10 - 2026.01 |
| 역할 | 프로그래머 |
| 주요 시스템 | CH2 SuperArio, CH3 grid와 editor, 건설과 생산, teleporter, Dancepace, dialogue와 interaction |

## 구현 내용

| 영역 | 주요 작업 |
| --- | --- |
| CH2 SuperArio | input, 이동, jump buffer, obstacle, stage, store, pipe, reward와 연출 |
| CH3 base | player movement, grid, minimap, 자원과 object interaction |
| Tile editor | placement, spawn point, block fill, 좌표 변환과 겹침 방지 |
| Building | build mode, factory, 생산, crafting과 inventory |
| Teleporter | region activation, list UI, fade와 distance close |
| Dancepace | wave data, input timing, character, UI와 sound presentation |
| Maintenance | reflection 제거, editor build 제외와 memory 정리 |

## SuperArio

횡스크롤 이동과 피격, obstacle spawn, coin과 item, 상점, pipe, stage와 reward 흐름을 구현했습니다. jump buffer와 input 교체, balancing과 연출까지 한 chapter 안에서 연결했습니다.

## Grid editor

기획자의 map 수정이 프로그래머 재배치와 build를 거치던 흐름을 Unity EditorWindow로 바꿨습니다. 기획자가 scene에서 object를 편집하고 Play로 바로 확인할 수 있습니다.

강제 Repaint와 반복 reflection을 제거하고 `GridSystem` reference와 occupied-cell cache를 사용해 Editor main thread frame time을 1084.8ms에서 52.7ms로 줄였습니다.
