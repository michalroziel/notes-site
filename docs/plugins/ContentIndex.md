---
title: ContentIndex
tags:
  - plugin/emitter
---

This [[plugin]] emits both RSS and an XML sitemap for your site. The [[RSS Feed]] allows users to subscribe to content on your site and the sitemap allows search engines to better [[my-notes-site/docs/index|index]] your site. The [[plugin]] also emits a `contentIndex.json` file which is used by dynamic frontend components like search and graph.

This [[plugin]] emits a comprehensive [[my-notes-site/docs/index|index]] of the site's content, generating additional resources such as a sitemap, an [[RSS Feed]], and a

> [!note]
> For information on how to add, remove or configure plugins, see the [[configuration#Plugins|Configuration]] page.

This [[plugin]] accepts the following [[configuration]] options:

- `enableSiteMap`: If `true` (default), generates a sitemap XML file (`sitemap.xml`) listing all site URLs for search engines in content discovery.
- `enableRSS`: If `true` (default), produces an [[RSS Feed]] (`[[my-notes-site/docs/index|index]].xml`) with recent content updates.
- `rssLimit`: Defines the maximum number of entries to include in the [[RSS Feed]], helping to focus on the most recent or relevant content. Defaults to `10`.
- `rssFullHtml`: If `true`, the [[RSS Feed]] includes full HTML content. Otherwise it includes just summaries.
- `rssSlug`: Slug to the generated [[RSS Feed]] XML file. Defaults to `"[[my-notes-site/docs/index|index]]"`.
- `includeEmptyFiles`: If `true` (default), content [[Files]] with no [[Body]] text are included in the generated [[my-notes-site/docs/index|index]] and resources.

## API

- Category: Emitter
- Function name: `[[plugin]].ContentIndex()`.
- Source: [`quartz/plugins/emitters/contentIndex.ts`](https://github.com/jackyzha0/quartz/blob/v4/quartz/plugins/emitters/contentIndex.ts).
