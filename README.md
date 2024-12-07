Randomly selects a player, his task is to survive for a certain time. The task remaining is to kill him. The winner gets a reward.

## Permissions

- `runningman.admin` -- Allows use of the admin commands

## Chat Commands

### Admin Commands

- `/eventon <PlayerName/PlayerID>` -- Start the running man *(required special rights depend on what you set on config file)* PlayerName/PlayerID is optional
- `/eventoff` -- Start the running man *(required special rights depend on what you set on config file)*
- `/running <k|killer> add <Package Name> <ItemName or money or karma> <MinAmount> <MaxAmount>` -- Create package if not exist and add item
- `/running <k|killer> remove <PackageName> <ItemName or karma or money>` -- Remove item from a package

### Player Commands

- `/run` -- Show the status of the event

## Console Commands

- `eventon` -- Start the running man *(requires admin access)*
- `eventoff` -- Stop the running man *(requires admin access)*

## Configuration

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

In this part, if "Random" is set to true, the system will take a reward from the data file list, if it is set to false it will use the "RewardFixing" and "RewardFixingAmount".

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

* **authLevel** is for both console commands eventon & eventoff, if you set it to 1, all user with auth level 1 and 2 will have access to command.
* **AutoStart** if set to true, the event will auto start at reload.
* **Block clans kill reward** if set to 1 and clans is loaded, clan kill reward will be blocked.
* **Block friends kill reward** if set to 1 and clans is loaded, friend kill reward will be blocked.
* **ChatName** is the name that appear infront of each message from lang file.
* **Count** is the minimum players needed to launch the event.
* **DisconnectPendingTimer** timer length, enabled when a runner is getting disconnect.
* **AutoStart** if set to true will start the timer after a plugin reload or after a restart.
* **Display Distance** is here to allow owner to display or not distance for the command /run.
* **Excluded auth level** to exclude moderator and admin set to 1, to exclude admin set to 2, to include everyone set to 0.
* **PauseeventTime** is the waiting time between 2 event (in minutes).
* **StarteventTime** is the time a player have to kill the runner, if runner isn't killed after this delay he will receive a reward (in minutes).

```json
  "TimeRange": {
    "Start War Time": 18,
    "End War Time": 8,
    "Enable Time Range": false
  }
```

* **TimeRange** Config for time range, used to allow event between start and end time
* **Enable Time Range** Used to enable the restriction.

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

* **CompassUI Info** * Compass placement and dicretion words
* **Countdown** * Countdown UI placement
* **Disable while event is off** * When set to true, disable the compass if there is no event running 

## Stored Data

Rewards are stored in `data/RunningMan.json`. Deleting this file would wipe all rewards.

If you want to edit item to runner list, just change k to r from the first arg. 

```json
{
  "runner": {
    "Karma": {
      "RewardItems": {
        "Karma": {
          "MinValue": 0,
          "MaxValue": 1
        }
      }
    },
    "Money": {
      "RewardItems": {
        "Money": {
          "MinValue": 100,
          "MaxValue": 1000
        }
      }
    },
    "ServerReward": {
      "RewardItems": {
        "serverreward": {
          "MinValue": 0,
          "MaxValue": 1
        }
      }
    },
    "build": {
      "RewardItems": {
        "wood": {
          "MinValue": 1000,
          "MaxValue": 10000
        },
        "stones": {
          "MinValue": 1000,
          "MaxValue": 10000
        }
      }
    }
  },
  "killer": {
    "Karma": {
      "RewardItems": {
        "Karma": {
          "MinValue": 0,
          "MaxValue": 1
        }
      }
    },
    "Money": {
      "RewardItems": {
        "Money": {
          "MinValue": 100,
          "MaxValue": 1000
        }
      }
    },
    "ServerReward": {
      "RewardItems": {
        "serverreward": {
          "MinValue": 0,
          "MaxValue": 1
        }
      }
    },
    "build": {
      "RewardItems": {
        "wood": {
          "MinValue": 1000,
          "MaxValue": 10000
        },
        "stones": {
          "MinValue": 1000,
          "MaxValue": 10000
        }
      }
    }
  }
}
```

## Localization

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
  "NobodyOnline": "<color=#C4FF00>{0}</color>: You can't run event while there is nobody online",
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
