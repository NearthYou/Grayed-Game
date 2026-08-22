# Teleporter system 설정

CH3 teleporter는 BaseCamp와 세 필드 지역을 연결합니다. 처음 방문한 타워를 활성화하고 현재 위치를 제외한 활성 지역만 UI에 보여줍니다.

## 현재 source 계약

| 항목 | 값 또는 동작 |
| --- | --- |
| region | `BaseCamp`, `Michael`, `Farmer`, `Dollar` |
| 기본 활성 지역 | `BaseCamp` |
| 표시 순서 | BaseCamp, Michael, Farmer, Dollar |
| interaction range | 2m |
| teleport delay | 0.1초 |
| UI close | 플레이어가 interaction range를 벗어나면 0.1초 간격으로 확인해 닫음 |
| 이동 중 입력 | `IsTeleporting`과 `CanInteract`로 중복 interaction 차단 |

별도 3초 cooldown과 UI close distance field는 현재 source에 없습니다.

## scene 구성

### TeleporterManager

scene에 `TeleporterManager` component를 가진 object를 하나 둡니다. manager는 지역별 타워, 활성 상태와 list order를 관리합니다.

### TeleportUI

Canvas object에 `TeleportUI`를 추가하고 다음 reference를 연결합니다.

- `Region List Panel`: 지역 list panel GameObject
- `Region List Content`: button parent Transform
- `Region Button Prefab`: Button과 TextMeshProUGUI를 가진 prefab
- `Cancel Button`: list를 닫는 button
- region name field: BaseCamp, Farmer, Dollar, Michael의 표시 이름

region button은 모든 enum value를 한 번 만들고 활성 list에 포함된 button만 보여줍니다.

### Teleporter

각 타워에 `Teleporter` component를 둡니다.

BaseCamp 타워 설정:

- `Region`: `BaseCamp`
- `Is Main Teleporter`: enabled
- 게임 시작 시 자동 활성

필드 타워 설정:

- `Region`: `Michael`, `Farmer`, `Dollar` 중 하나
- `Is Main Teleporter`: disabled
- 처음 interaction할 때 활성

공통 field:

- `Interaction Range`: 기본 2
- `Teleport Delay`: 기본 0.1

### Button prefab

```text
RegionButton (Button)
└─ Text (TextMeshProUGUI)
```

## 동작 순서

1. 플레이어가 비활성 타워와 interaction하면 해당 지역을 활성 상태로 등록합니다.
2. 현재 지역을 제외한 활성 지역을 manager priority 순서로 가져옵니다.
3. `TeleportUI`가 해당 button만 보여줍니다.
4. 플레이어가 region을 선택하면 UI를 닫고 fade out을 시작합니다.
5. target tower의 grid position 아래 cell로 플레이어를 옮깁니다.
6. fade in과 0.1초 delay 뒤 두 타워의 interaction state를 reset합니다.

main tower 외에 활성 지역이 없으면 BaseCamp UI를 열지 않습니다. target tower를 찾지 못한 경우에도 이동하지 않습니다.

## distance close

UI를 연 타워는 현재 플레이어와의 squared distance를 0.1초 간격으로 확인합니다. 거리가 `interactionRange`보다 커지면 UI를 닫고 current interactor를 지웁니다.

별도 close distance를 inspector에서 맞출 필요가 없습니다. interaction range가 UI close 기준도 함께 소유합니다.

## fade와 position

scene에 `FadeController`가 있으면 fade out과 fade in duration을 기다립니다. controller가 없어도 position change는 진행합니다.

target position은 target tower의 `GridPosition`에서 y grid를 한 칸 줄인 위치입니다. 플레이어에 Rigidbody가 있으면 velocity를 지우고 `rb.position`을 바꾸며, 없으면 Transform position을 사용합니다.

## code check

```csharp
bool active = TeleporterManager.Instance.IsTeleporterActivated(
    TeleportRegion.Farmer);

Teleporter target = TeleporterManager.Instance.GetTeleporter(
    TeleportRegion.BaseCamp);
```

setup이 source와 어긋나면 다음 파일을 함께 확인합니다.

- `Teleporter.cs`
- `TeleporterManager.cs`
- `TeleportUI.cs`
- `GridSystem.cs`
