# Community Check-Ins Configuration

Editable settings are stored as arguments inside the imported Streamer.bot actions.

Only edit values inside groups labeled:

```text
****** Settings ******
```

Do not edit groups labeled:

```text
****DO NOT EDIT****
```

## Community Check-in

### `checkInSuccessMessage`

Sent when one or more new check-ins are recorded.

Default:

```text
Thanks @{user} for checking in to: {communities}!
```

Available tags:

- `{user}`
- `{communities}`

### `alreadyCheckedInMessage`

Sent when all selected communities were already recorded for the current date.

Default:

```text
@{user}, you’ve already checked in to: {communities} today.
```

Available tags:

- `{user}`
- `{communities}`

### `invalidSelectionMessage`

Sent when the reward input does not contain a valid community number.

Default:

```text
@{user}, please include one or more valid community numbers.
```

Available tag:

- `{user}`

### `todayFileEntry`

Controls each entry in a community's readable Today text file.

Default:

```text
@{user}
```

Available tags:

- `{user}`
- `{community}`
- `{date}`

## Auto Check-in

### `autoCheckInMessage`

Sent after a viewer is automatically checked into prior communities.

Default:

```text
@{user}, you have been automatically checked in to: {communities}!
```

Available tags:

- `{user}`
- `{communities}`

### `todayFileEntry`

Controls entries written when an automatic check-in rebuilds a Today text file.

Use the same formatting as the `Community Check-in` action to keep files consistent.

## Checkins Lookup Permissions

### `allowTargetLookup`

Master switch for `!checkins @username`.

### Role switches

- `allowBroadcaster`
- `allowModerators`
- `allowVIPs`
- `allowSubscribers`
- `allowRegularViewers`

A requester must match an enabled role to look up another viewer. A viewer may always use `!checkins` for their own totals.

## Checkins Lookup Messages

### `userTotalsMessage`

Default:

```text
🏆 @{user} | Check-ins today: {today} | Total check-ins: {entries}
```

Available tags:

- `{user}`
- `{today}`
- `{entries}`
- `{total}`

### `userTotalsEntry`

Controls each community/count entry inserted into `{entries}`.

Default:

```text
{community} ({count})
```

Available tags:

- `{community}`
- `{count}`
- `{user}`

### `userTotalsSeparator`

Placed between user-total entries.

Default:

```text
 | 
```

### `userNoCheckinsMessage`

Default:

```text
@{user} has no recorded check-ins.
```

Available tags:

- `{user}`
- `{today}`
- `{total}`

## Leaderboard Formatting

### `leaderboardSize`

Number of users displayed on a community leaderboard.

Supported range:

```text
1-50
```

Default:

```text
10
```

### `leaderboardHeader`

Default:

```text
🏆 {community} Check-In Leaderboard: 
```

Available tags:

- `{community}`
- `{count}`

### `leaderboardEntry`

Default:

```text
#{rank} @{user} ({count})
```

Available tags:

- `{rank}`
- `{user}`
- `{count}`
- `{community}`

### `leaderboardSeparator`

Placed between leaderboard entries.

Default:

```text
 | 
```

### `leaderboardEmptyMessage`

Default:

```text
{community} has no recorded check-ins yet.
```

Available tag:

- `{community}`

## Lookup Error Messages

### `targetLookupDisabledMessage`

Used when targeted lookup is disabled globally.

Available tags:

- `{requester}`
- `{user}`

### `targetLookupPermissionMessage`

Used when the requester does not have permission to inspect another viewer.

Available tags:

- `{requester}`
- `{user}`

### `communityNotFoundMessage`

Used when a supplied community name or number cannot be resolved.

Available tags:

- `{requester}`
- `{input}`

## Community Management

Communities are managed through chat instead of action arguments:

```text
!community list
!community add Community Name
!community remove Community Name
!community rename Old Name | New Name
!community move CurrentNumber NewNumber
```

Community names and ordering are stored in:

```text
Omanges Extensions/Community Check-Ins/CommunitySettings.json
```

Manual editing of this JSON file is not recommended while Streamer.bot is running.

## Reward Prompt

The **Update Check-in Reward Prompt** action builds the prompt from the current community list.

Confirm that its reward-update sub-action targets the same reward assigned to **Community Check-in**. The action is also run automatically when the community manager changes the list.