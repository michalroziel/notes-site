---
title: Recent Notes
tags: component
---

Quartz can generate a list of recent notes based on some filtering and sorting criteria. Though this [[component]] isn't included in any [[layout]] by default, you can add it by using `[[component]].RecentNotes` in `quartz.[[layout]].ts`.

## Customization

- Changing the title from "Recent notes": pass in an additional parameter to `[[component]].RecentNotes({ title: "Recent writing" })`
- Changing the number of recent notes: pass in an additional parameter to `[[component]].RecentNotes({ limit: 5 })`
- Display the note's tags (defaults to true): `[[component]].RecentNotes({ showTags: false })`
- Show a 'see more' link: pass in an additional parameter to `[[component]].RecentNotes({ linkToMore: "tags/components" })`. This field should be a full slug to a page that exists.
- Customize filtering: pass in an additional parameter to `[[component]].RecentNotes({ filter: someFilterFunction })`. The filter function should be a function that has the signature `(f: QuartzPluginData) => boolean`.
- Customize sorting: pass in an additional parameter to `[[component]].RecentNotes({ sort: someSortFunction })`. By default, Quartz will sort by date and then tie break lexographically. The sort function should be a function that has the signature `(f1: QuartzPluginData, f2: QuartzPluginData) => number`. See `byDateAndAlphabetical` in `quartz/components/PageList.tsx` for an example.
- [[component]]: `quartz/components/RecentNotes.tsx`
- Style: `quartz/components/styles/recentNotes.scss`
