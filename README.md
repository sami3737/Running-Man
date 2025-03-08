
# Running Man Event

The "Running Man" event randomly selects a player, whose task is to survive for a certain period. Other players are tasked with killing the runner before time runs out. The player who kills the runner will receive a reward.

## Permissions

- **`runningman.admin`**: Grants the user access to admin commands.

## Chat Commands

### Admin Commands

- `/eventon <PlayerName/PlayerID>`: Starts the Running Man event for the specified player. *(Requires special rights as configured)*
- `/eventoff`: Stops the Running Man event. *(Requires special rights as configured)*
- `/running <k|killer> add <PackageName> <ItemName|money|karma> <MinAmount> <MaxAmount>`: Creates a new package or adds an item to an existing package.
- `/running <k|killer> remove <PackageName> <ItemName|karma|money>`: Removes an item from a package.

### Player Commands

- `/run`: Displays the current status of the event.

## Console Commands

- `eventon`: Starts the Running Man event. *(Requires admin access)*
- `eventoff`: Stops the Running Man event. *(Requires admin access)*

## Configuration

### Reward Settings

```json
"Reward": {
  "Random": true,
  "RewardFixing": "wood",
  "RewardFixingAmount": 10000,
  "KarmaSystem": {
    "PointToRemove": 0,
    "PointToAdd": 1
  }
}
```

- **Random**: If `true`, a random reward is selected from a predefined list. If `false`, the fixed reward (e.g., wood) is given.
- **RewardFixing**: Defines the fixed reward type (e.g., "wood").
- **RewardFixingAmount**: Defines the amount for the fixed reward.
- **KarmaSystem**: Defines the points added or removed based on karma actions.

### Event Settings

```json
"Default": {
  "ChatName": "EVENT",
  "authLevel": 1,
  "AutoStart": true,
  "Display Distance": true,
  "Count": 2,
  "StarteventTime": 30,
  "PauseeventTime": 30,
  "DisconnectPendingTimer": 30,
  "Excluded auth level": 1,
  "Block friends kill reward": true,
  "Block clans kill reward": true
}
```

- **authLevel**: Sets the required authorization level to execute `/eventon` and `/eventoff` commands.
- **AutoStart**: If `true`, the event auto-starts when the plugin reloads or the server restarts.
- **Count**: Minimum number of players needed to start the event.
- **StarteventTime**: Time limit (in minutes) for the runner to survive before receiving a reward.
- **PauseeventTime**: Time (in minutes) between two consecutive events.
- **Display Distance**: If `true`, displays the distance to the runner using the `/run` command.

### Time Range Configuration

```json
"TimeRange": {
  "Start War Time": 18,
  "End War Time": 8,
  "Enable Time Range": false
}
```

- **Enable Time Range**: If `true`, limits the event to specific times (between `Start War Time` and `End War Time`).

### Compass UI Settings

```json
"CompassUI Info": {
  "AnchorMin": "0.03 0.067",
  "AnchorMax": "0.05 0.09",
  "Direction": {
    "North East": "N-E",
    "South East": "S-E",
    "North West": "N-W",
    "South West": "S-W",
    "No runner": "/"
  },
  "Disable while event is off": false
},
"Countdown Info": {
  "AnchorMin": "0.93 0.93",
  "AnchorMax": "1 1"
}
```

- **CompassUI Info**: Defines compass UI settings, including placement and directions.
- **Disable while event is off**: If `true`, the compass is disabled when the event is not running.
- **Countdown Info**: Defines the UI position for the countdown.

## Stored Data

Rewards are stored in `data/RunningMan.json`. Deleting this file will remove all saved rewards.

To edit an item in the runner's list, replace `k` with `r` in the first argument.

### Example Stored Data Structure

```json
{
  "runner": {
    "Karma": { "RewardItems": { "Karma": { "MinValue": 0, "MaxValue": 1 } } },
    "Money": { "RewardItems": { "Money": { "MinValue": 100, "MaxValue": 1000 } } },
    "ServerReward": { "RewardItems": { "serverreward": { "MinValue": 0, "MaxValue": 1 } } },
    "build": { "RewardItems": { "wood": { "MinValue": 1000, "MaxValue": 10000 }, "stones": { "MinValue": 1000, "MaxValue": 10000 } } }
  },
  "killer": {
    "Karma": { "RewardItems": { "Karma": { "MinValue": 0, "MaxValue": 1 } } },
    "Money": { "RewardItems": { "Money": { "MinValue": 100, "MaxValue": 1000 } } },
    "ServerReward": { "RewardItems": { "serverreward": { "MinValue": 0, "MaxValue": 1 } } },
    "build": { "RewardItems": { "wood": { "MinValue": 1000, "MaxValue": 10000 }, "stones": { "MinValue": 1000, "MaxValue": 10000 } } }
  }
}
```

## Localization

Customizable language strings for various events:

```json
{
  "StartEventRunner": "<color=#C4FF00>{0}</color>: Running man {1}\nKill him and get the reward!\nCommand: /run - to know the distance to the target.",
  "NotEnoughPlayers": "<color=#C4FF00>{0}</color>: There aren't enough players to start the event.",
  "RunnerSaved": "<color=#C4FF00>{0}</color>: {1} ran away from the chase and received a reward!",
  "StillRunner": "<color=#C4FF00>{0}</color>: {1} your are still the runner.",
  "RunnerBackOnline": "<color=#C4FF00>{0}</color>: {1} is back online.\nKill him and get the reward!",
  "RunnerKilled": "<color=#C4FF00>{0}</color>: Player - {1} kill {2} and received a reward!",
  "RunnerDistance": "<color=#C4FF00>{0}</color>: Player - {1},\n is at a distance of {2}\nKill him and get the reward!",
  "UntilEndOfEvent": "<color=#C4FF00>{0}</color>: Until the end of event left: {1} minutes",
  "NotRunningEvent": "<color=#C4FF00>{0}</color>: At the moment the event is not running",
  "UntilStartOfEvent": "<color=#C4FF00>{0}</color>: Before the start of the event remained: {1} minutes",
  "RunCommandHelp": "Use \"/run\" to find out information about the running man",
  "AdminCommandHelp": "Use \"/eventon\" for start event Running Man\nUse \"/eventoff\" for start event Running Man",
  "AdminAddCommandHelp": "Use \"/running add <Package Name> <ItemName or money or karma> <MinAmount> <MaxAmount>\" to add item.",
  "AdminRemoveCommandHelp": "Use \"/running remove <PackageName> <ItemName or karma or money>\" to remove item.",
  "NobodyOnline": "<color=#C4FF00>{0}</color>: You can't run an event while there is nobody online",
  "NoPerm": "<color=#C4FF00>{0}</color>: You have no rights to do this!",
  "RunnerLeaved": "<color=#C4FF00>{0}</color>: {1} got scared and ran away!",
  "EventStopped": "<color=#C4FF00>{0}</color>: Event has stopped!",
  "PackageDontExist": "<color=#C4FF00>{0}</color>: This package don't exist.",
  "MissingItemFromPackage": "<color=#C4FF00>{0}</color>: Item not found in package.",
  "ItemRemoved": "<color=#C4FF00>{0}</color>: Successfully removed item {1}.",
  "ItemAdded": "<color=#C4FF00>{0}</color>: Successfully added item {1} to package {2}.",
  "PackageAdded": "<color=#C4FF00>{0}</color>: Successfully added package {1} and inserted item to it.",
  "ItemExist": "<color=#C4FF00>{0}</color>: Item already exist in package.",
  "Rewarded": "<color=#C4FF00>{0}</color>: You won a reward : {1}."
}
```

