# Omanges Community Check-Ins

**Omanges Community Check-Ins** is a custom-built extension for [Streamer.bot](https://streamer.bot) that allows Twitch streamers to track viewer engagement across multiple communities. This system supports manual check-ins via channel point rewards and automatic check-ins based on chat activity, storing logs in a lightweight, easy-to-edit `.txt` format.

---

## 🎯 Key Features

- 🔘 **Multi-Community Check-In System**  
  Viewers can check into one or more Twitch communities like `SIDOR`, `Pizza Party`, and `Bullet Fam` in a single interaction.

- 🤖 **Automatic First-Chat Check-In**  
  When a viewer sends their first chat of the stream, the bot will automatically check them in to any communities they’ve previously been associated with.

- 📝 **Simple `.txt` Logging**  
  Each community is logged to a separate `.txt` file (e.g., `SIDOR.txt`, `Pizza Party.txt`) with one line per user, keeping tracking easy and portable.

- 💬 **Dynamic Reward Prompt**  
  The channel point reward prompt updates in at the beginning of the stream to reflect the list of available communities, pulled from a dictionary in the script.

- 🧪 **Stream Debug Mode**  
  Optional debug messages in chat or logs to verify that systems are working as expected.

---

## 🧰 Requirements

- [Streamer.bot v0.2.8 or later](https://streamer.bot)
- Twitch channel point reward set up
- Basic understanding of importing actions and scripts

---

## 📦 Installation

### 1. Import the Files
Download or clone this repository, then:

- Open Streamer.bot
- Go to `Actions` → `Import` → Select the `.sb` file included in this repo

### 2. Create Your Channel Point Reward
In the **Twitch Streaming** tab:

- Create a custom **Channel Point Reward** (name it anything you like, e.g., `Check-In`)
- Leave the prompt blank or enter anything — the script will auto-update it

### 3. Set Up the Folder Structure
Create a folder on your system (e.g., `CheckIns`) where `.txt` log files will be stored:

You do **not** need to create the folders or `.txt` files manually — they’ll be auto-generated when a user checks in.

---

## ⚙️ Configuration

You can customize communities and formatting directly in the script:

* Add, remove, or rename communities as needed.
* Change the `separator` for how the reward prompt appears (default is `" | "`).
* Update `checkInDirectory` if your folder path is different.
* Change how it's logged in chat or saved in the `.txt` files.

---

## 🔄 How It Works

### ✅ Viewer Redeems Check-In Reward

1. User redeems the reward.
2. Script logs their name into each relevant community’s `.txt` file.
3. If they're already checked in, they're skipped (no duplicates).
4. Reward prompt is updated at the beginning of stream to show all community names.

### 🗣️ Viewer Sends First Chat of Stream

1. The script scans all `.txt` files for their username.
2. If found, the user is re-logged (auto check-in) with a message sent in chat (optional).
3. This happens once per stream per user.

---

## 🧹 Maintenance

### 🔁 Reset All Check-In Logs

Use the included **Clear Check-In Logs** script to wipe all community `.txt` files in one click.

> ⚠️ Warning: This cannot be undone. Use with caution. Ensure to set the folder name correctly prior to use.

---

## 💡 Examples

### Example Prompt

```
Type the number(s) for the communities that you want to check in to: 0-SIDOR | 1-Pizza Party | 2-Bullet Fam
```

### Example SIDOR.txt

```
07/30/25 - Omanges
07/30/25 - TaraShark
07/30/25 - xX_GamerLlama_Xx
07/31/25 - Omanges
07/31/25 - DigitalOwen
```



## 🧑‍💻 Developer Notes

This system was built with flexibility and transparency in mind:

* **.txt file logging** keeps data readable and easy to migrate
* **No external API dependencies**
* **Fully extensible** – add webhooks, counters, overlays, and more

---

## 🤝 Contributing

You can also suggest ideas via [GitHub Issues](https://github.com/your-repo/issues).

---

## 📞 Support

Join the [SIDOR Community Discord](https://discord.gg/2pcKpMrxdD) to get help, suggest features, or just hang out with other creators using this system.

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

## 📂 Repository Structure

```plaintext
Omanges-Community-Check-Ins/
├── README.md
├── LICENSE
├── Omanges Community Check-ins.sb    # Streamer.bot importable action
```

```

---

Let me know if you’d like me to prep a real GitHub repo structure with `.sb` and `.cs` placeholders, or generate the LICENSE file and add a badge header for things like Twitch, C#, or MIT license.
```
