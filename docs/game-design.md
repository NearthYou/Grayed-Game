# Grayed Game 설계

## 핵심 경험

Grayed Game은 잊힌 게임이 떨어지는 회색 마을을 탐험하는 PC 2D adventure입니다. 주인공 라플리는 다른 게임의 규칙과 UI를 가져와 마을의 문제를 풀고, 플레이어는 chapter마다 달라지는 조작과 장르를 경험합니다.

핵심은 여러 mini game을 단순히 나열하는 데 있지 않습니다. 한 chapter의 main field에서 다른 게임의 규칙으로 접속했다가 다시 돌아오는 흐름이 세계관과 progression 안에 연결돼야 합니다.

## 메타픽션 세계관

마을에는 기억에서 사라진 game과 resource가 떨어집니다. 시간이 지나면 색과 형태를 잃는다는 설정이 회색 화면과 장르 전환의 시각적 근거가 됩니다.

라플리는 현재 플레이어가 조작하고 있어 완전히 잊히지 않은 game입니다. 이 차이를 이용해 마을의 주민, 사라지는 resource와 각 chapter의 규칙을 연결합니다.

2024년 작업 초안의 미완성 5개 chapter, placeholder story와 GameOver 가제는 현재 설계로 사용하지 않습니다. 이 문서는 실제 README와 구현된 CH3, Dancepace 범위만 설명합니다.

## 장르 결합 구조

main chapter는 탐험, 대화와 interaction을 담당합니다. 접속 콘텐츠는 다른 조작과 화면 규칙을 가진 mini game으로 구성합니다.

현재 저장소에서 확인되는 대표 범위는 다음과 같습니다.

- top-down exploration과 NPC interaction
- CH3 grid field, building, production과 resource collection
- Dancepace 리듬 미니게임
- Yarn Spinner dialogue와 event trigger
- 지역을 연결하는 teleporter 시스템

## CH3 건설과 자원 흐름

CH3 main field는 2.5D grid를 사용합니다. `CH3_LevelData`가 object type, footprint, sprite와 collision 정보를 정의하고 `GridSystem`이 occupied cell, movement와 spawn state를 관리합니다.

editor에서 배치한 object와 Play 중 `BuildingObjectFactory`가 만드는 건물은 같은 데이터 계약을 사용합니다. 기획자가 배치한 필드와 runtime 건물이 다른 규칙으로 움직이는 문제를 줄이기 위한 구조입니다.

플레이어는 자원을 수집해 건물을 만들고 생산 item을 얻습니다. inventory, hotbar, tooltip과 sound feedback은 이 loop를 화면에 연결합니다.

## Dancepace 리듬 미니게임

Dancepace는 key input, wave progression, time limit와 result panel을 가진 rhythm mini game입니다.

wave와 게임 설정은 ScriptableObject에 두고 string table과 연결합니다. rehearsal, answer character, audience effect와 sound는 game flow state에 따라 나뉩니다.

input 판정과 presentation을 한 class에 몰지 않고 manager, data, character, effect와 UI 단위로 나눈 것이 현재 source의 경계입니다.

## 현재 구현 범위

- Unity 2022.3.62f2 기반 PC 프로젝트
- chapter별로 다른 장르와 system을 결합하는 구조
- CH3 필드 editor와 runtime grid
- building, production, resource, inventory와 hotbar
- teleporter activation, region list와 fade transition
- Dancepace data, input judgment와 presentation
- dialogue, NPC interaction과 event area
