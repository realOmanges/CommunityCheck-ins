# Community Check-Ins Setup Guide

## 1. Download and Import

1. Download the latest `.sb` file from the repository's GitHub Releases page.
2. Open Streamer.bot.
3. Click **Import**.
4. Drag the `.sb` file into the import window.
5. Complete the import.

The imported action group is:

```text
Omanges - Community Check-Ins
```

## 2. Review the Imported Actions

The extension contains these actions:

| Action | Purpose |
|---|---|
| `Community Check-in` | Processes the Twitch channel-point redemption. |
| `Auto Check-in` | Checks returning viewers in when their first chat trigger runs. |
| `Checkins Lookup` | Handles `!checkins` totals, targeted lookups, and leaderboards. |
| `Community Manager` | Handles `!community` management commands. |
| `Update Check-in Reward Prompt` | Rebuilds the reward prompt from the current community list. |
| `Clear Check-in Logs` | Deletes check-in histories when run manually. Disabled by default. |

Version 2.4.2 and newer do not contain an **Initialize / Repair** action or automatic startup initializer.

## 3. Configure the Channel-Point Reward

1. Create or select the Twitch channel-point reward used for check-ins.
2. Open the **Community Check-in** action.
3. Assign that reward to the channel-point trigger.
4. Open **Update Check-in Reward Prompt**.
5. Select the same reward in the reward-update sub-action.
6. Run **Update Check-in Reward Prompt** once to verify the prompt.

The viewer should enter one or more community numbers separated by spaces, such as:

```text
1 4 8
```

## 4. Enable and Restrict Commands

The imported commands are disabled by default.

### `!checkins`

Enable this command for normal viewers after reviewing the targeted-user lookup permissions inside the **Checkins Lookup** action.

### `!community`

Restrict this command to the broadcaster and trusted moderators. It can change the community list and archive community data.

## 5. Add Your Communities

Use the community manager command:

```text
!community add Community Name
```

Repeat for each community, then verify the order:

```text
!community list
```

The displayed number is the number viewers enter in the channel-point reward.

The primary data folder is created as needed at:

```text
<Streamer.bot>/Omanges Extensions/Community Check-Ins/
```

## 6. Test the Extension

### Test a manual check-in

1. Redeem the configured reward from a test account.
2. Enter one or more valid community numbers.
3. Confirm the success response in chat.
4. Confirm the JSON and Today text files were created.

### Test duplicate prevention

Redeem the same community again on the same date. The extension should report that the viewer is already checked in.

### Test viewer totals

```text
!checkins
```

### Test a community leaderboard

```text
!checkins 1
```

or:

```text
!checkins Community Name
```

### Test targeted lookup permissions

```text
!checkins @username
```

Test from accounts with different Twitch roles to confirm the configured permissions.

### Test community persistence

1. Add a temporary test community.
2. Run several other commands.
3. Confirm the community remains in `CommunitySettings.json`.
4. Remove the test community when finished.

Version 2.4.2 fixes the v2.4.1 race condition that could revert newly saved community changes.

## 7. Updating from v1.2.0 or Another Legacy Version

1. Back up both folders if they exist:

```text
Omanges Extensions/Check-Ins/
Omanges Extensions/Community Check-Ins/
```

2. Import the new extension.
3. Disable or remove duplicated legacy actions and commands only after confirming the new actions work.
4. Reassign the channel-point reward where required.
5. Run a normal check-in or community-management command so required files and supported legacy migration can be handled.
6. Verify that communities and history were migrated.
7. Enable the new commands.

Do not delete the backup until the new JSON histories have been verified.