# ✅ Omanges Community Check-Ins

**Omanges Community Check-Ins** is a Streamer.bot extension for tracking viewer engagement across multiple Twitch communities.

Viewers can check into one or more communities through a channel-point reward, returning members can be checked in automatically from their first chat message, and broadcasters can manage communities without editing C# code.

---

## 🎯 Key Features

- ✅ **Multi-Community Check-Ins**  
  Viewers can select one or more communities in a single channel-point redemption.

- 🤖 **Automatic Check-Ins**  
  Returning viewers can be automatically checked into their previously associated communities when they first chat.

- 🏆 **Community Leaderboards**  
  Use `!checkins <community>` to display the top members of a community.

- 👤 **Viewer Check-In Lookups**  
  Use `!checkins` to view your own totals, or `!checkins @username` when lookup permissions allow it.

- 🛠️ **In-Chat Community Management**  
  Add, remove, rename, reorder, and list communities with the `!community` command.

- 💬 **Customizable Formatting**  
  Chat responses, leaderboard entries, separators, and text-file formatting can be edited through Streamer.bot arguments.

- 🔐 **Configurable Lookup Permissions**  
  Choose whether broadcasters, moderators, VIPs, subscribers, or regular viewers may look up another user.

- 🔄 **Automatic Reward Prompt Updates**  
  The extension rebuilds the channel-point reward prompt whenever the community list changes.

- 🧰 **Initialization and Legacy Migration**  
  Required folders and files are created automatically, with migration support for older `.txt`-based versions.

---

## 🧰 Requirements

- [Streamer.bot](https://streamer.bot) **1.0.0-alpha.1 or newer**
- A Twitch account connected to Streamer.bot
- A Twitch channel-point reward used for community check-ins

---

## 📦 Installation

### 1. Download the Extension

Download the latest `.sb` file from the repository's [GitHub Releases](../../releases/latest) page.

### 2. Import into Streamer.bot

1. Open Streamer.bot.
2. Click **Import**.
3. Drag the downloaded `.sb` file into the import window.
4. Complete the import.

The imported action group is named:

```text
Omanges - Community Check-Ins
```

### 3. Assign the Channel-Point Reward

Assign your check-in reward to the imported **Community Check-in** action, then select the same reward in **Update Check-in Reward Prompt**.

### 4. Enable the Commands

The imported commands are disabled by default. Review their permissions and then enable:

```text
!checkins
!community
```

Detailed setup instructions are available in [`docs/SETUP.md`](docs/SETUP.md).

---

## 💬 Commands

### Viewer Commands

| Command | Description |
|---|---|
| `!checkins` | Displays the requesting viewer's check-in totals. |
| `!checkins @username` | Displays another viewer's totals when the requester has permission. |
| `!checkins <community>` | Displays the leaderboard for a community name or number. |

### Community Management Commands

| Command | Description |
|---|---|
| `!community list` | Lists the current community numbers and names. |
| `!community add Community Name` | Adds a new community. |
| `!community remove Community Name` | Removes a community and archives its data files. |
| `!community rename Old Name \| New Name` | Renames a community and its data files. |
| `!community move 4 1` | Moves a community from one numbered position to another. |

> Restrict `!community` to the broadcaster and trusted moderators through Streamer.bot command permissions.

---

## ⚙️ Configuration

Editable settings are grouped near the top of the imported actions. Do not modify sections labeled:

```text
****DO NOT EDIT****
```

You can configure:

- Check-in success, duplicate, and invalid-selection messages
- Automatic check-in messages
- User lookup responses
- Leaderboard size, header, entry format, and separator
- Permission levels for `!checkins @username`
- Today-file entry formatting

See [`docs/CONFIGURATION.md`](docs/CONFIGURATION.md) for all available arguments and tags.

---

## 🔄 How It Works

### Viewer Redeems the Check-In Reward

1. The viewer enters one or more community numbers.
2. The extension validates each selection.
3. New check-ins are added to each community's JSON history.
4. Duplicate check-ins for the same viewer and date are skipped.
5. The readable `Today.txt` file is rebuilt for each affected community.
6. A formatted response is sent to chat.

### Viewer Sends Their First Chat Message

1. The extension finds communities previously associated with the viewer.
2. The viewer is checked into those communities for the current date.
3. Existing same-day entries are not duplicated.
4. A formatted automatic check-in response is sent to chat.

### Community List Changes

When a community is added, removed, renamed, or moved through `!community`, the settings file is saved and the reward prompt is rebuilt automatically.

---

## 📁 Files Created

The extension stores its data beneath the Streamer.bot installation directory:

```text
Omanges Extensions/
└── Community Check-Ins/
    ├── CommunitySettings.json
    ├── Community Name.json
    ├── Community Name - Today.txt
    ├── Archived Communities/
    └── migration and initialization markers
```

### Community JSON Files

Each community receives a JSON file containing its date-based check-in history.

### Today Text Files

Each community also receives a readable `- Today.txt` file generated from the current day's check-ins.

### Archived Communities

Removing a community moves its existing JSON and Today files into `Archived Communities` instead of permanently deleting them.

> Back up the entire `Omanges Extensions/Community Check-Ins` folder before moving Streamer.bot, reinstalling it, or replacing your computer.

---

## 🔼 Updating from an Older Version

1. Back up your existing `Omanges Extensions/Check-Ins` and `Omanges Extensions/Community Check-Ins` folders.
2. Import the current `.sb` release.
3. Review duplicated commands and actions before enabling the new versions.
4. Run **Initialize / Repair** manually if migration does not run automatically.
5. Confirm the channel-point reward assignments.
6. Review the new formatting and permission settings.

The extension can migrate legacy community `.txt` files into JSON history and copies supported files from the older `Omanges Extensions/Check-Ins` directory.

---

## 🧹 Maintenance

### Initialize or Repair

Run **Initialize / Repair** to recreate required folders, repair missing files, and migrate supported legacy data.

### Clear Check-In Logs

The included **Clear Check-in Logs** action deletes all community JSON histories and legacy text logs. It is disabled by default.

> ⚠️ This reset cannot be undone. Back up your data first.

---

## 🛠️ Troubleshooting

### The reward prompt shows the wrong communities

Confirm that **Update Check-in Reward Prompt** has the correct reward selected, then run the action manually.

### `!checkins @username` is denied

Review the permission arguments in **Checkins Lookup** and verify that target lookups are enabled for the requester's role.

### A community name is not recognized

Run `!community list` and use the current community number or exact name.

### Data was not migrated from an older version

Back up both check-in folders, then run **Initialize / Repair** and review the Streamer.bot logs for migration errors.

### The commands do nothing

Confirm that both imported commands are enabled and still connected to their corresponding actions.

---

## 📞 Support and Feedback

- Open a bug report or feature request through this repository's GitHub Issues.
- Join the [SIDOR Community Discord](https://discord.gg/2pcKpMrxdD) for help or discussion.

---

## 👤 Author

**Omanges**  
🟣 [Twitch.tv/Omanges](https://twitch.tv/omanges)  
💬 [SIDOR Community Discord](https://discord.gg/2pcKpMrxdD)

---

## 📄 License

Released under the [MIT License](LICENSE).

You are free to use, modify, and share this extension while retaining appropriate credit.