# yaml-tags-discord-bot

This is more of a personal project intended to be used in the Wabbajack community to run search queries and to answer questions in discord. But can possibly be useful for other communities that need tags that post answers to for example frequently asked questions or contain some instructions for common fixes or similar things.

## How to use

### Get a Bot-Token

Follow this guide to get a Token for your Bot:
https://docs.pycord.dev/en/stable/discord.html

When you invite the bot to your server make sure you use the `OAuth2` tool to generate the proper invite link with the following settings:  
![image](https://github.com/EzioTheDeadPoet/mdBookSearchBot/assets/52624146/ac5701fb-e7dc-44f6-8c57-d44897ade50b)  
![image](https://github.com/EzioTheDeadPoet/mdBookSearchBot/assets/52624146/d736d11e-55fc-4394-bfaa-65c7310e144b)

### Configuration Environment Variables

- `DISCORD_BOT_TOKEN` Needs to be set to the bot token
- `TAG_INDEX_GET` raw url to a YAML file or a rest api that sends a YAML body

### Example Configuration

Docker-Compose.yaml:
```yaml
services:
  yaml-tags-discord-bot:
    image: eziothedeadpoet/yaml-tags-discord-bot:latest
    env_file:
      - .env
      - secrets.env
    restart: unless-stopped
```

.env:
```dotenv
TAG_INDEX=https://raw.githubusercontent.com/EzioTheDeadPoet/tag_repository/master/tags.yaml
```

secrets.env (needs to be created):
```dotenv
DISCORD_BOT_TOKEN=COPY_TOKEN_HERE
```

## How to configure tags

Tags are configured in a YAML file:  
```yaml
tag: 
  text: https://link.to.raw/tag.md
  image_url: https://link.to/image.png
```
*Setting an `image_url` is optional.*
