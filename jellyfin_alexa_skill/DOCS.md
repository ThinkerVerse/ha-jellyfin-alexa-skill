# Jellyfin Alexa Skill

## How to use

This add-on allows you to use Alexa voice commands to play media from your Jellyfin server. It creates a bridge between Amazon's Alexa service and your Jellyfin server.

### Prerequisites

Before setting up this add-on, you need:

1. A running Jellyfin server that is accessible via the internet (or a method to make it accessible)
2. An Amazon Developer account
3. Home Assistant with a valid SSL certificate and domain name
4. Home Assistant instance that is accessible from the internet
5. Optionally, the MariaDB add-on (recommended for better persistence)

### Initial Setup

#### 1. Amazon Developer Account Setup

1. **Create an Amazon Developer Account**:
   - Go to [developer.amazon.com](https://developer.amazon.com/) and create an account

2. **Create a New Alexa Skill**:
   - Go to the Alexa Developer Console
   - Click "Create Skill"
   - Name your skill (e.g., "Jellyfin Player")
   - Choose "Custom" model
   - Choose "Provision your own" for the backend resources
   - Click "Create skill"

3. **Set Up Account Linking**:
   - In your skill's dashboard, go to "Account Linking" in the left menu
   - Set Authorization URI to: `https://your-skill-endpoint.com/authorizationData`
   - Set Access Token URI to: `https://your-skill-endpoint.com/accessToken`
   - Set Client ID to a random string (you'll need this later)
   - Set Client Secret to a random string (you'll need this later)
   - Add scope: `jellyfin`
   - Privacy Policy URL: Can be any valid URL for testing

4. **Create a Security Profile for SMAPI Access**:
   - Install the ASK CLI: `npm install -g ask-cli`
   - Run `ask configure` and follow the prompts to generate a refresh token

#### 2. Add-on Installation

1. Add this repository to your Home Assistant instance
2. Install the "Jellyfin Alexa Skill" add-on
3. Configure the add-on with the information from your Amazon Developer account
4. Start the add-on

#### 3. Account Linking

1. Open the Alexa app on your mobile device
2. Go to "Skills & Games"
3. Select "Your Skills"
4. Find and select your skill
5. Click "Enable" to start the account linking process
6. Log in with your Jellyfin credentials

### Configuration Options

| Option | Description |
|--------|-------------|
| `jellyfin_endpoint` | The public URL of your Jellyfin server (must be accessible) |
| `skill_endpoint` | The public URL for the skill (must be accessible from the internet) |
| `skill_endpoint_ssl_cert_type` | Type of SSL certificate (trusted, wildcard, or self_signed) |
| `skill_id` | Your Alexa skill ID from the Amazon Developer Console |
| `client_id` | Client ID from Amazon Developer account |
| `client_secret` | Client secret from Amazon Developer account |
| `refresh_token` | Refresh token from ASK CLI |
| `database.user` | Database username |
| `database.password` | Database password |
| `database.database` | Database name |
| `database.host` | Database host (use "core-mariadb" for the MariaDB add-on) |
| `database.port` | Database port |
| `invocation_names.en_US` | English (US) invocation name (optional) |

### Voice Commands

Once setup is complete, you can use commands like:

- "Alexa, ask Jellyfin Player to play music by [artist]"
- "Alexa, ask Jellyfin Player to play [movie title]"
- "Alexa, ask Jellyfin Player to play my favorites"
- "Alexa, ask Jellyfin Player to pause"
- "Alexa, ask Jellyfin Player to resume"

For a complete list of commands, see the [jellyfin-alexa-skill wiki](https://github.com/infinityofspace/jellyfin_alexa_skill/wiki).

## Troubleshooting

### Common Issues

1. **Account Linking Fails**:
   - Make sure your skill endpoint is correctly configured and accessible
   - Check that the SSL certificate is valid and trusted

2. **Skill Doesn't Find Media**:
   - Verify that your Jellyfin server is accessible at the URL provided
   - Check that your media is properly organized and tagged in Jellyfin

3. **Database Connection Issues**:
   - If using the MariaDB add-on, make sure it's running
   - Check that the database credentials are correct

### Logs

The add-on logs can help diagnose issues. To view logs:

1. Go to the add-on's Info page
2. Click on the "Log" tab

## Support

If you encounter issues with this add-on:

1. Check the [jellyfin-alexa-skill GitHub issues](https://github.com/infinityofspace/jellyfin_alexa_skill/issues)
2. Open an issue on the add-on repository if it's specific to Home Assistant integration

## Additional Resources

- [Jellyfin Alexa Skill GitHub Repository](https://github.com/infinityofspace/jellyfin_alexa_skill)
- [Jellyfin Alexa Skill Wiki](https://github.com/infinityofspace/jellyfin_alexa_skill/wiki)
- [Amazon Alexa Skills Kit Documentation](https://developer.amazon.com/en-US/docs/alexa/ask-overviews/what-is-the-alexa-skills-kit.html)