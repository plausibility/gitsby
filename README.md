The Great Gitsby
================

Handle git commit hooks like a champ.

The general idea behind Gitsby is similar to that of danneu's [captain-githook](https://github.com/danneu/captain-githook) - you provide a config file (either explicity through the `GITSBY_CONFIG` env var, or `~/gitsby/gitsby.json` by default) and Gitsby will handle commit hooks from both BitBucket and GitHub for you.

# gitsby.json

```json
{
	"landing": true,
	"repos": [
		{"url": "https://github.com/plausibility/example.git"},
		{
			"url": "git@bitbucket.com:plausibility/example.git",
			"directory": "~/foobarbaz",
			"hidden": true
		}
	]
}
```

The general idea is you provide two (currently) things: whether or not you want a `landing` page, and a list of `repos`.  
The repos MUST contain at least a `url`, but MAY also contain a `directory` (where they'll be cloned, default is `~/gitsby/{{ project-name }}` from url), and whether or not they're `hidden` on the landing page.

# Hook endpoints
There are currently two (planned) endpoints: `/github` and `/bitbucket` - guess what they're designed to receive the payloads for?  
At the moment, Gitsby will only bind to `0.0.0.0:9999` - this is planned to change via either command line flags, config variables or env vars. I'm not 100% certain yet.
