# Anchor Marketplace

The public skill catalog for [Anchor](https://github.com/Majidul17068/anchor),
the desktop client for Google's Antigravity CLI. There is no server: Anchor
downloads `index.json` from this repository and installs skills from it.

## Publish a skill

In Anchor, open the skill under **Skills → Mine** and choose **Publish**.
Anchor validates it, writes `listing.json` and a zip, and opens a prefilled
issue here. Attach both files to the issue. A maintainer reviews it and adds
it to `index.json` (and `skills/<slug>/` for browsing on GitHub).

You can also open a pull request that adds the listing to `index.json`
directly; follow the schema in
[docs/MARKETPLACE.md](https://github.com/Majidul17068/anchor/blob/main/docs/MARKETPLACE.md).

## Request a skill

**Marketplace → Requests → New request** in Anchor, or open a
[request issue](../../issues/new?template=request.yml).

## Layout

```
index.json                 the catalog Anchor reads
skills/<slug>/             source folders of accepted skills
bundles/<slug>.zip         optional zips referenced by bundleUrl
.github/ISSUE_TEMPLATE/    submission, request and review forms
```

Listings must be MIT or another OSI license, must not contain secrets, and
must have a SKILL.md with `name` and `description` frontmatter.
