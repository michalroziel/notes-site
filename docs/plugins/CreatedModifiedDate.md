---
title: "CreatedModifiedDate"
tags:
  - plugin/transformer
---

This [[plugin]] determines the created, modified, and published dates for a document using three potential data sources: [[Frontmatter]] metadata, Git [[my-notes-site/node_modules/workerpool/HISTORY|HISTORY]], and the filesystem. See [[authoring content#Syntax]] for more information.

> [!note]
> For information on how to add, remove or configure plugins, see the [[configuration#Plugins|Configuration]] page.

This [[plugin]] accepts the following [[configuration]] options:

- `priority`: The data sources to consult for date information. Highest priority first. Possible values are `"[[Frontmatter]]"`, `"git"`, and `"filesystem"`. Defaults to `["[[Frontmatter]]", "git", "filesystem"]`.

When loading the [[Frontmatter]], the value of [[Frontmatter#List]] is used.

> [!warning]
> If you rely on `git` for dates, make sure `defaultDateType` is set to `modified` in `quartz.config.ts`.
>
> Depending on how you [[hosting|host]] your Quartz, the `filesystem` dates of your local [[Files]] may not match the final dates. In these cases, it may be better to use `git` or `[[Frontmatter]]` to guarantee correct dates.

## API

- Category: Transformer
- Function name: `[[plugin]].CreatedModifiedDate()`.
- Source: [`quartz/plugins/transformers/lastmod.ts`](https://github.com/jackyzha0/quartz/blob/v4/quartz/plugins/transformers/lastmod.ts).
