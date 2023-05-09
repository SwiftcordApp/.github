<img src="res/swiftcord_new_icon.png" height="128" align=right>


# Swiftcord

A beautiful and blazingly fast native macOS Discord client, built in SwiftUI.

<img width=100% src="res/hero.webp">

#### Nightly Build
[![Nightly build action status](https://img.shields.io/github/actions/workflow/status/SwiftcordApp/Swiftcord/build.yaml.svg?style=for-the-badge)](https://nightly.link/SwiftcordApp/Swiftcord/workflows/build.yaml/main/swiftcord-canary.zip)

#### Releases

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/cryptoAlgorithm/Swiftcord?style=for-the-badge)](https://github.com/cryptoAlgorithm/Swiftcord/releases/)

---

<p>
<img src="res/discordKit_icon.png" height="128" align=left>
<h1>DiscordKit</h1>

The missing Swift Discord library. Build elegant Discord bots with a simple resultBuilder-powered
slash command builder.
</p>

Here's all you need to build a bot with DiscordKit (it's that simple):
```swift
import DiscordKitBot

let bot = Client(intents: .unprivileged)

// Guild to register commands in. If the COMMAND_GUILD_ID environment variable is set, commands are scoped
// to that server and update instantly, useful for debugging. Otherwise, they are registered globally.
let commandGuildID = ProcessInfo.processInfo.environment["COMMAND_GUILD_ID"]

bot.ready.listen {
    print("Logged in as \(bot.user!.username)#\(bot.user!.discriminator)!")

    try? await bot.registerApplicationCommands(guild: commandGuildID) {
        NewAppCommand("ping", description: "Ping me!") { interaction in
            try? await interaction.reply("Pong!")
        }
    }
}

bot.login() // Reads the bot token from the DISCORD_TOKEN environment variable and logs in with the token

// Run the main RunLoop to prevent the program from exiting
RunLoop.main.run()
```
