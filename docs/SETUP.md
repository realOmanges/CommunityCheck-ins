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
| `Initialize / Repair` | Creates required files and migrates supported legacy data. |
| `Update Check-in Reward Prompt` | Rebuilds the reward prompt from the current community list. |
| `Clear Check-in Logs` | Deletes check-in histories when run manually. Disabled by default. |

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

## 5. Initialize the Extension

The **Initialize / Repair** action includes an initialization trigger, but it may also be run manually.

Run it manually after importing when:

- Updating from an older release
- Required folders do not appear
- Legacy `.txt` history needs migration
- A community file is missing or damaged

The primary data folder is:

```text
<Streamer.bot>/Omanges Extensions/Community Check-Ins/
```

## 6. Add Your Communities

Use the community manager command:

```text
!community add Community Name
```

Repeat for each community, then verify the order:

```text
!community list
```

The displayed number is the number viewers enter in the channel-point reward.

## 7. Test the Extension

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

## 8. Updating from v1.2.0 or Another Legacy Version

1. Back up both folders if they exist:

```text
Omanges Extensions/Check-Ins/
Omanges Extensions/Community Check-Ins/
```

2. Import the new extension.
3. Disable or remove duplicated legacy actions and commands only after confirming the new actions work.
4. Run **Initialize / Repair**.
5. Verify that communities and history were migrated.
6. Reassign the channel-point reward where required.
7. Enable the new commands.

Do not delete the backup until the new JSON histories have been verified.