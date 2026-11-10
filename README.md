# AnimaGuru

AnimaGuru is the animation production studio, powered by AI. This plugin connects Claude to your AnimaGuru account and adds every AnimaGuru film skill.

## What's included

- **The AnimaGuru connector** (`https://animaguru.com/mcp`): your projects, films, gallery folders, brand kits, film templates, the asset library, avatars and generation jobs. Every generation shows a credit estimate first, and jobs can be tracked or canceled without submitting them twice.
- **The AnimaGuru Studio**, an interactive app in the conversation on Claude's web, desktop and mobile apps. Find and preview projects, play films and keep them beside the chat, file them in folders, inspect animation frames and quality findings, and pick characters, media, brand kits and library assets for a film. It speaks English, Turkish, Swedish and Arabic.
- **Skills** for making animated films with the AnimaGuru CLI: explainer, advertisement and general video workflows, 60 animation styles, Art Motion with 36 art treatments and nine explainer grammars, brand kits, branching stories, quizzes, presentations, 3D models and clip prompts, plus PixiJS v8 references.

## Install

In Claude Code:

```
/plugin marketplace add Docyrus/animaguru-claude-plugin
/plugin install animaguru@animaguru
```

Then run `/mcp`, choose `plugin:animaguru:animaguru` and sign in to AnimaGuru. The same marketplace is also served at `https://animaguru.com/claude/marketplace.json`.

In Claude on the web or desktop, add the GitHub marketplace `Docyrus/animaguru-claude-plugin` under **Customize → Plugins** and install AnimaGuru, then add the AnimaGuru connector on the plugin's **Connectors** tab and sign in.

## Account

Signing in uses OAuth; you never paste a password or API key into the chat. AnimaGuru's tools need Individual Starter, Individual Pro or Team, and every account starts with a 7-day Individual Pro trial. Generation spends your AnimaGuru credits.

- Setup guide: https://animaguru.com/agent-setup
- Support: https://animaguru.com/support
- Privacy policy: https://animaguru.com/privacy-policy
- Terms of service: https://animaguru.com/terms-of-service

## License

MIT, © Docyrus, Inc. Some skills keep their own licenses; see NOTICE.md.
