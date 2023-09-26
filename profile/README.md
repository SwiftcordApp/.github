# Contact Us!

Wanna talk about Swiftcord/Discord or just hang around? Join us in Discord!

<a aria-label="Join the community on Discord" href="https://discord.gg/he7n6MGDXS" target="_blank">
  <img alt="" src="https://img.shields.io/discord/964741354112577557?style=for-the-badge&labelColor=black&label=Discord%20Server">
</a>

<img src="/res/swiftcord_new_icon.png" height="128" align=right>

# [Swiftcord](https://github.com/SwiftcordApp/Swiftcord)

A beautiful and blazingly fast native macOS Discord client, built in SwiftUI.

<img width=100% src="/res/hero.webp">

### Downloads

Give Swiftcord a try! Nightly builds (recommended) are built from every commit on `main`, while releases are more stable but updated less frequently.

[![Nightly build action status](https://img.shields.io/github/actions/workflow/status/SwiftcordApp/Swiftcord/build.yaml.svg?style=for-the-badge&label=Nightly%20Build)](https://nightly.link/SwiftcordApp/Swiftcord/workflows/build.yaml/main/swiftcord-canary.zip)&nbsp;&nbsp;[![GitHub release (latest by date)](https://img.shields.io/github/v/release/cryptoAlgorithm/Swiftcord?style=for-the-badge)](https://github.com/cryptoAlgorithm/Swiftcord/releases/)

---

<img src="/res/discordKit_icon.png" height="128" align=left>

# [DiscordKit](https://github.com/SwiftcordApp/DiscordKit)

The missing Swift Discord library. Build elegant Discord bots with a simple resultBuilder-powered
slash command builder.

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
