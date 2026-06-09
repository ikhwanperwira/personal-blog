# personal-blog

This repository is the source of truth for `https://blog.mip.my.id`.

## Publishing model

The publishing branch is `main`.

Every push to `main`:

1. Runs CI to validate the Hugo site build.
2. Is picked up by the OCI VM deployment agent.
3. Rebuilds the site on the VM.
4. Replaces the live site only when the build succeeds.

If a build fails, the currently published site stays in place.

## Local development

Requirements:

- Hugo Extended

Run locally:

```bash
hugo server
```

Build locally:

```bash
hugo --gc --minify
```

## Create a new post

```bash
hugo new content/posts/my-post.md
```

## Repository structure

- `hugo.toml`: site configuration
- `archetypes/default.md`: default front matter for new posts
- `content/posts/`: blog posts
- `layouts/`: custom templates
- `static/css/site.css`: site styling
- `.github/workflows/ci.yml`: CI validation
