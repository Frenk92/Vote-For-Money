This allows you to reward the players who vote the server. For now only works on **Rust-Servers.net**, **TopRustServers.com** and **TrackyServer.com**, but if you want, I'll try to add other sites. Please report any bugs. Thank you.

**[ Please, if you like my works and you want that I continue to upgrade them, considered you making a donation, also small. Thank you so much. ]**

## Features
* *Economics*, *RP* (Server Rewards) and *Kits* rewards.
* Add commands as rewards.
* Different rewards for the various groups (Example *vip* or *donator*).
* Choose a time interval between votes.
* Choose rewards interval between votes
* Automatically give rewards on players login.
* Prevent to use the vote for a period's time after a wipe.
* Rewards for top voters. (COMING SOON)

## Permissions
Admin: `voteformoney.admin`
## Commands
```      
/vote - check if you voted and get you the rewards.      
/claimkit - claim all kits not received the first time.  
```
## Admin Commands
**Chat & Console**
### Config
```
editvote check "true/false:OPTIONAL" - turn on/off vote checker at login.
editvote alldefault "true/false:OPTIONAL" - enable/disable default kit for all groups.
editvote prefix "Text" - edit default prefix.
editvote block "Days.Hours" - edit the blocking time of the vote after a wipe. ("0.0" = disabled)
```
### Rewards
```
vr set "Name.Interval" - select a group reward to edit (Example: vr set default.1)
vr add group "Name.Interval" - add new group reward (Example: vr add group vip.1).
vr add money/rp/kit "Value" - add new reward to the selected group.
vr add cmd "Name" "Command" - add new command reward to the selected group.
vr remove group "Name.Interval" - remove group reward.
vr remove money/rp/kit - remove reward from the selected group.
vr remove cmd "Name" - remove command reward from the selected group.
vr edit money/rp/kit "NewValue" - edit the reward if it exists in the selected group.
vr edit cmd "Name" "NewValue" - edit command reward if it exists in the selected group.
vr list groups - show groups reward list.
vr list rewards - show rewards list of the selected group.
```
**The added group is automatically selected.**

## Configuration
```json
{
  "InitCheck": true,
  "AllGroupsGetDefault": false,
  "Prefix": "<color=#808000ff><b>VoteForMoney:</b></color>",
  "BlockVote": "0.6"
}
```
**Info:**
*  "InitCheck" = vote checker at login.
*  "AllGroupsGetDefault" = default kit for all groups.
*  "Prefix" = prefix of plugin messages.
*  "BlockVote" = prevent to use the vote for a period's time after a wipe ("0.0" = disabled).

## Data Config
> The folder can be found in *oxide/data/VoteForMoney*
### Rewards
Edit with what you prefer and remove unnecessary things.

**Default**
```json
{
  "Groups": {
    "default.1": {
      "money": "250",
      "rp": "30",
      "kit": ""
    },
    "default.2": {},
    "vip.1": {}
  },
  "TopVoters": {
    "1": {
      "money": "1000",
      "rp": "100",
      "kit": ""
    },
    "2": {},
    "3": {}
  }
}
```
**Example**
```json
{
  "Groups": {
    "default.1": { //group.interval
      "money": "250",
      "rp": "30",
      "kit": "vote",
      "pro": "usergroup add $player.id pro" //Command rewards. Can use $player.id or $player.name. "commandname": "command"
    },
    "default.2": {
      "kit": "supply"
    },
    "vip.1": {
      "money": "400",
      "rp": "50",
      "kit": "vipvote",
    }
  },
  "TopVoters": {
    "1": {},
    "2": {},
    "3": {}
  }
}
```
### Sites
**Default**
```json
{
  "Rust-Servers": {
    "ID": "",
    "Key": "",
    "Interval": "1.0"
  },
  "TopRustServers": {
    "ID": "",
    "Key": "",
    "Interval": "1.0"
  },
  "TrackyServer": {
    "ID": "",
    "Key": "",
    "Interval": "1.0"
  }
}
```
**Info:** "Interval": "days.hours"

## Localization
```json
{
  "Thanks": "Thanks for voting on {0}",
  "RewardCoins": "Coins reward: {0}",
  "RewardRP": "RP reward: {0}",
  "RewardKit": "All Kits rewarded.",
  "RewardCommand": "{0} rewarded.",
  "NextVote": "Next Vote: {0}",
  "NoVote": "You have not voted yet on {0}.\nLink to vote: {1}{2}",
  "AlreadyVoted": "You have already voted on {0}.",
  "AlreadyClaimed": "You have already claimed all kits.",
  "AlreadyExists": "This reward already exists.",
  "Edited": "\"{0}\" edited to: {1}",
  "Selected": "Group \"{0}\" has been selected.",
  "GroupAdded": "Group \"{0}\" has been added.",
  "GroupRemoved": "Group \"{0}\" has been removed.",
  "RewardAdded": "Reward \"{0}\" has been added.",
  "RewardRemoved": "Reward \"{0}\" has been removed.",
  "GroupsList": "Groups list: {0}",
  "RewardsList": "\"{0}\" rewards list: {1}",
  "NoPlugin": "Plugin \"{0}\" not loaded.",
  "NoGroup": "Group \"{0}\" doesn't exist.",
  "NoKit": "Kit \"{0}\" doesn't exist.",
  "NoReward": "Reward \"{0}\" not found.",
  "NotFound": "Group \"{0}\" not found.",
  "NotSelected": "Group not selected. Use \"/vr set\" to select one (Example: /vr set default.1).",
  "NoAnswer": "No answer from {0}. Try later.",
  "NoConfig": "Could not read config file. Creating new one...",
  "ConsNoAnswer": "Error: {0} - Couldn't get an answer from {1}",
  "MissingArg": "One or more arguments are missing.",
  "ErrorBool": "Error. Only 'true' or 'false'.",
  "ErrorKits": "Not all kits have been redeemed. Empty the inventory and redeem them with \"/claimkit\".",
  "InvalidReward": "\"{0}\" is an invalid reward.",
  "InvalidArg": "\"{0}\" is an invalid argument.",
  "InvalidValue": "\"{0}\" is an invalid value.",
  "SecondsFormat": "The vote is blocked for {0} second/s.",
  "MinutesFormat": "The vote is blocked for {0} minute/s.",
  "HoursFormat": "The vote is blocked for {0} hour/s.",
  "DaysFormat": "The vote is blocked for {0} day/s."
}
```