# 코드와 자료

README에서 설명한 플레이와 구현을 바로 확인할 수 있는 자료를 모았습니다.

## 실행 환경

| 항목 | 내용 |
| --- | --- |
| Unity | 2022.3.62f2 |
| 시작 장면 | `Assets/Scenes/Title.unity` |
| 플레이 영상 | [YouTube](https://www.youtube.com/watch?v=fdvunwIGKAs) |
| 실행 파일 | [Google Drive](https://drive.google.com/file/d/1NscghxWgvjWWtu2stNFduW3cMFrBb4fl/view?usp=sharing) |

## 플레이 장면

| 구간 | 영상 |
| --- | --- |
| 탐험과 건설 | [0분 44초부터 보기](https://youtu.be/fdvunwIGKAs?t=44) |
| 플랫포머 | [1분 24초부터 보기](https://youtu.be/fdvunwIGKAs?t=84) |
| 리듬 게임 | [1분 59초부터 보기](https://youtu.be/fdvunwIGKAs?t=119) |

## 구현별 코드

| 내용 | 코드 |
| --- | --- |
| 맵 직접 배치와 겹침 확인 | [맵 제작 도구](../Assets/Scripts/Editor/GridTileEditor.cs) |
| 편집 화면과 실제 게임이 공유하는 설정 | [맵 설정 데이터](../Assets/Scripts/Runtime/CH3/Main/Data/CH3_LevelData.cs) |
| 칸 좌표와 배치 상태 | [좌표 관리](../Assets/Scripts/Runtime/CH3/Main/Core/GridSystem.cs) |
| 플랫포머 화면 전환 | [진행 상태](../Assets/Scripts/Runtime/CH2/SuperArio/ArioManager.cs) |
| 플랫포머 장애물 재사용 | [장애물 관리](../Assets/Scripts/Runtime/CH2/SuperArio/ObstacleManager.cs) |
| 리듬 입력 판정 | [게임 진행과 판정](../Assets/Scripts/Runtime/CH3/Dancepace/Managers/GameFlowManager.cs) |
| 리듬 패턴 | [패턴 데이터](../Assets/Scripts/Runtime/CH3/Dancepace/Data/WaveDataSO.cs) |

## 팀 결과

- 2024 BIC Rookie 부문 온오프라인 전시
- 2024 LOGIN 대학생 연합 발표회 기획 우수상

팀 구성과 참여 기간은 [담당 범위](contributions.md)에 정리했습니다.
