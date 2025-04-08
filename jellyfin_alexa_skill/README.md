# Home Assistant Add-on: Jellyfin Alexa Skill

This add-on allows you to use Alexa voice commands to play media from your Jellyfin server.

## About

This add-on integrates [jellyfin-alexa-skill](https://github.com/infinityofspace/jellyfin_alexa_skill) with Home Assistant, allowing you to control your Jellyfin media library using Amazon Alexa voice commands.

With this skill, you can:
- Play music, movies, and TV shows from your Jellyfin server
- Create and manage playlists
- Control playback (pause, resume, skip)
- Adjust volume

The add-on runs the self-hosted portion of the skill, which acts as a bridge between Amazon's Alexa service and your Jellyfin server.

## Installation

Follow these steps to set up the add-on:

1. Add this repository to your Home Assistant instance
2. Install the "Jellyfin Alexa Skill" add-on
3. Configure the required options (see below)
4. Start the add-on
5. Activate the skill in your Alexa app and link your Jellyfin account

## Configuration

### Amazon Developer Account Setup

Before using this add-on, you need to:

1. Create an Amazon Developer Account
2. Create a new Alexa skill (Custom model)
3. Set up account linking for the skill
4. Create a security profile for SMAPI access

Detailed instructions can be found in the [jellyfin-alexa-skill wiki](https://github.com/infinityofspace/jellyfin_alexa_skill/wiki).

### Add-on Configuration

```yaml
jellyfin_endpoint: "https://your-jellyfin-server.com"  # Public URL of your Jellyfin server
skill_endpoint: "https://your-domain.com"              # Public URL for the skill (must be accessible from the internet)
skill_endpoint_ssl_cert_type: "trusted"                # SSL certificate type (trusted, wildcard, or self_signed)
skill_id: "amzn1.ask.skill.your-skill-id"              # Your Alexa skill ID
client_id: "your-client-id"                            # Client ID from Amazon Developer console
client_secret: "your-client-secret"                    # Client secret from Amazon Developer console
refresh_token: "your-refresh-token"                    # Refresh token from ASK CLI
database:
  user: "skill"                                        # Database user (default: skill)
  password: "jellyfin"                                 # Database password
  database: "jellyfin_alexa_skill"                     # Database name
  host: "core-mariadb"                                 # Database host (use core-mariadb for the MariaDB addon)
  port: 3306                                           # Database port
invocation_names:                                      # Custom invocation names (optional)
  en_US: "jellyfin player"                             # English (US) invocation name
  # de_DE: "jellyfin spieler"                          # German invocation name (optional)
  # ja_JP: "jellyfin プレーヤー"                         # Japanese invocation name (optional)
```

### Network Requirements

- Your Home Assistant instance must be accessible from the internet on port 1456
- You need a domain with a valid SSL certificate (Let's Encrypt works well)
- Your Jellyfin server must also be accessible (either publicly or through the same network as this add-on)

## Support

If you have any issues with this add-on, please:

1. Check the [jellyfin-alexa-skill issues page](https://github.com/infinityofspace/jellyfin_alexa_skill/issues)
2. Open an issue on this repository if it's related to the Home Assistant integration

## License

This add-on is based on [jellyfin-alexa-skill](https://github.com/infinityofspace/jellyfin_alexa_skill) which is licensed under GPL-3.0.