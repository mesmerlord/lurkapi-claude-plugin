# LurkAPI for Claude

[LurkAPI](https://lurkapi.com) is a social media scraping API. This plugin connects Claude to it, so you can scrape TikTok, Instagram, YouTube, Reddit, X (Twitter), Facebook and more from a conversation: a creator's profile, a video's transcript, a Reddit thread or the ads a brand is running come back as clean JSON.

LurkAPI runs the scrapers, proxies and parsers, so there's no headless browser, proxy pool or blocked IP on your side. It scrapes public pages only and never logs in to anyone's account.

![LurkAPI](./logo.png)

## What you can scrape

- **TikTok**: profiles, videos, transcripts, comments, hashtags, sounds, stories, lives, TikTok Shop products and the EU ad library
- **Instagram**: profiles, posts, reels, comments and transcripts of reels
- **YouTube**: videos, transcripts, comments, channels, Shorts and search
- **Reddit**: subreddit feeds, search and full comment threads
- **Facebook**: Meta Ad Library search, every ad an advertiser runs, pages and posts
- **Google**: the Ads Transparency Center (advertisers and their ads)
- **X (Twitter), Threads, Bluesky, Truth Social, Telegram, Snapchat, LinkedIn** (company pages and ad library) and **Linktree**

That's 60+ endpoints, all read-only. The [docs](https://lurkapi.com/docs) list every one with its parameters and a real response.

## Set up

1. Install the plugin.
2. Connect LurkAPI when Claude asks (in Claude Code, run `/mcp` and pick LurkAPI). A LurkAPI page opens: sign in with Google or your email, or create a free account in the same step. New accounts get 100 free credits, and a balance below 25 is topped back up to 25 every day.
3. Click **Allow**. Claude gets its own LurkAPI API key, named after it, so there's nothing to copy or paste.

Then ask Claude things like:

- "What ads is Gymshark running on Facebook right now? Summarize the angles."
- "Get the transcript of this YouTube video and pull out the main claims."
- "Compare the follower counts of these five TikTok creators."
- "Find Reddit threads from the last month about switching from Notion to Obsidian, and summarize the complaints."

Claude finds the right endpoint with `find_endpoints` and runs it with `call_endpoint`, so the 60+ endpoints don't crowd your context.

## Cost

Most calls cost 1 credit; each tool's description shows its price, and every result shows your remaining balance. A call that reaches the platform is charged even when the thing isn't found; server errors are free. Credit packs start at $9 for 10,000 credits and never expire. See [pricing](https://lurkapi.com/pricing).

## Data

The plugin has no local code. It registers one remote MCP server, `https://api.lurkapi.com/mcp`, which you connect by signing in to LurkAPI with OAuth. LurkAPI then creates an API key for Claude, which Claude sends with each call; revoke it in your [dashboard](https://lurkapi.com/dashboard) to disconnect. When Claude calls a tool, the tool's parameters (for example a username, a video URL or a search keyword) go to LurkAPI, which fetches the matching public pages and returns them as JSON. LurkAPI never logs in to anyone's account and returns only publicly available data.

LurkAPI logs each call (endpoint, parameters, result code, credits; never your key) for 14 days for support and abuse prevention, and doesn't keep the data it returned. See the [privacy policy](https://lurkapi.com/privacy) and [terms](https://lurkapi.com/terms).

## Support

Email [support@lurkapi.com](mailto:support@lurkapi.com) or open an [issue](https://github.com/mesmerlord/lurkapi-claude-plugin/issues). LurkAPI is made by Mesmer s.r.o.

## License

MIT
