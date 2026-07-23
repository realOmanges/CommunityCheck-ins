# Changelog

All notable changes to **Omanges Community Check-Ins** are documented here.

## [2.4.1] - 2026-07-23

### Added

- `!community` management command with support for listing, adding, removing, renaming, and reordering communities.
- Community leaderboards through `!checkins <community>`.
- Other-user lookup support through `!checkins @username`.
- Role-based lookup permissions for broadcasters, moderators, VIPs, subscribers, and regular viewers.
- Editable message, leaderboard, separator, and Today-file formatting through Streamer.bot arguments.
- **Initialize / Repair** action for creating folders, repairing missing files, and migrating supported legacy data.
- `CommunitySettings.json` for persistent community ordering and configuration.
- Per-community JSON history files.
- Readable per-community `- Today.txt` files.
- `Archived Communities` folder for preserving files when a community is removed.
- Automatic reward-prompt rebuilding after community-management changes.

### Changed

- Standardized the imported action group name to `Omanges - Community Check-Ins`.
- Updated the minimum supported Streamer.bot version to `1.0.0-alpha.1`.
- Replaced the legacy `.txt`-only history system with date-based JSON history while retaining readable Today files.
- Moved data storage to `Omanges Extensions/Community Check-Ins`.
- Organized editable action arguments into clearly labeled settings groups.
- Added protected `****DO NOT EDIT****` sections for internal action logic.
- Expanded `!checkins` from a personal lookup command into user totals, targeted lookups, and community leaderboards.

### Migration

- Copies supported files from the legacy `Omanges Extensions/Check-Ins` directory.
- Converts supported legacy community `.txt` logs into JSON history.
- Removes migrated legacy text files after successful conversion where appropriate.
- Uses migration markers to prevent duplicate migrations.

## [1.2.0]

### Existing Features

- Multi-community check-ins through a Twitch channel-point reward.
- Automatic check-ins based on a viewer's first chat message.
- Basic `!checkins` lookup command.
- Dynamic reward-prompt updates.
- Manual log-clearing action.
- Community history stored in individual `.txt` files.

[2.4.1]: ../../releases/tag/v2.4.1