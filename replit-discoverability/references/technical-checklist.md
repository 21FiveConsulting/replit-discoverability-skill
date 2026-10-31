# Technical verification checklist

Use this as a menu of checks, not a mandate to scan every route on every minor edit. Adapt to the project's stack, site type, and user-approved scope.

## URL and routing
- [ ] Inventory: indexable public / public noindex / authenticated / admin / API / assets / redirects / unknown paths.
- [ ] Consistent scheme and preferred host; non-preferred host redirects when feasible, otherwise canonical signals consistent and limitations documented.
- [ ] Consistent trailing slash, lowercase and query-param policy, including internal navigation and sitemap.
- [ ] On large or parameterized sites, prevent crawl traps from faceted filters, internal search, session IDs, and unbounded query combinations; verify pagination behavior where it applies.
- [ ] Status 200 on canonical public pages, 3xx on aliases, 404/410 on truly missing pages; no false 200 SPA route.
- [ ] Public paths are accessible without credentials; private routes/data protected by authorization, not crawler directives.
- [ ] `robots.txt` references correct sitemap(s), doesn't inadvertently block indexable routes or critical render resources.
- [ ] Check both HTML robots directives and response-header `X-Robots-Tag` on representative HTML and non-HTML resources; resolve conflicting or inherited directives.
- [ ] XML sitemap returns 200, uses absolute canonical public URLs, excludes utility/private routes, and is maintained automatically or through a clear update process.
- [ ] For multilingual/regional pages, use correct document language and valid, reciprocal `hreflang` relationships where needed; keep language/region URLs and canonicals consistent.

## Initial HTML and hydration
- [ ] In fetched initial HTML for each representative page: actual title, meaningful content and links, page-specific description, one canonical, correct robots directives, semantic H1, appropriate schema.
- [ ] JS disabled / blocked test on key pages: primary information is readable; CTA links not intentionally hidden behind animation/hydration.
- [ ] Browser hydration retains title, canonical, robots, schema count, content, anchors, and app functionality. Avoid duplicate or contradictory metadata.
- [ ] Dynamic/private client shells don't inherit generic public-page canonical or index directives.
- [ ] Distinguish Google crawler support for JS from other engines/AI retrieval systems' variable JS abilities. Prerendering is an engineering default where appropriate, not a universal platform mandate.

## Content and machine readability
- [ ] Unique factual title and description fit search intent; one clear H1; H2/H3 hierarchy supports reading and screenreader navigation.
- [ ] Direct answers, scannable sections, accurate citations and claims, genuine author/publisher details and verified update dates where relevant.
- [ ] Descriptive internal links in body content; avoid orphan pages and unnecessary redirect hops.
- [ ] Accurate Organization / LocalBusiness / Service / Article / Breadcrumb / FAQPage JSON-LD **only where appropriate**; match visible facts and Google's current eligibility constraints.
- [ ] No fake `datePublished`, `dateModified`, reviews, ratings, awards, author credentials, prices or addresses; verify source.
- [ ] Optional `llms.txt`: if requested, accurate public links, brand identity and non-sensitive content. Not an official Google indexing submission, nor evidence of AEO/GEO ranking.
- [ ] If AI crawler access is in scope, identify the publisher's intent separately for search/retrieval and training crawlers; verify current official bot names and policy behavior before changing `robots.txt` or other access controls. Do not assume robots directives control every crawler or guarantee AI citations.
- [ ] Consistent social preview metadata and a properly sized brand-approved social image.
- [ ] If image/video discovery matters, check that important media is crawlable, has useful contextual text or captions where appropriate, and uses a sitemap only when it adds value; do not expose private media.

## Accessibility and user experience
- [ ] Useful landmarks, labels, alt descriptions for informative images, keyboard operability, visible focus, logical tab order, appropriate ARIA and announcements.
- [ ] Text contrast using *actual* foreground and composited background: >= 4.5:1 normal, >= 3:1 large, with relevant WCAG exceptions. Review hover/focus/disabled state appropriately.
- [ ] Decorative brand colors need not become body-text colors; preserve approved palette while ensuring legibility.
- [ ] Zoom not disabled; font sizes/wrapping usable on narrow screens; no horizontal overflow or content clipping.
- [ ] `prefers-reduced-motion`; no essential content initially hidden awaiting a slow JS animation.
- [ ] Accordion/form/CTA functionality remains after semantic or styling changes.

## Performance
- [ ] Measured FCP/LCP/CLS/INP if possible with conditions, cold/warm cache, browser version, network, sample count, and comparison baseline.
- [ ] Hero/LCP image not inadvertently lazy; below-fold large images lazy where appropriate; width/height and responsive sources; optimize without replacing brand/user-supplied creative.
- [ ] Initial text, CTA and skeleton content visible without unnecessary JS-dependent entrance animation.
- [ ] Assess font CSS and network timing before self-host/async changes; font swap may create CLS.
- [ ] Check actual JS transfer and route-specific imports. Splitting code must preserve SSR/SSG and client/auth flows; avoid speculative refactors for mere build-size warnings.
- [ ] Hashed asset caching and freshness of HTML/API responses; validate live reverse-proxy behavior, not origin headers alone.

## Validation matrix
- [ ] Build/typecheck/lint and diff check on files changed (use commands already defined by project).
- [ ] Verify targeted public pages initial HTTP HTML and browser rendering (desktop/phone) and important interactions.
- [ ] Confirm sitemap, robots and canonicals only if changed or risked by change.
- [ ] Check representative 404, API, client/auth route noindex and no-store when routing/build changed; use test accounts, never real client data for optimization testing.
- [ ] For changes to DNS/host redirects, validate main host and alternate host, query parameters, deep links, auth callback routes, and caching/CDN.
- [ ] Report deployment status truthfully, then verify live; do not conflate local testing with successful deployment.
- [ ] Obtain actual Search Console evidence before concluding Google indexed, declined or chose a canonical URL.

## Primary references (verify currency as needed)
- Replit Agent skills: https://docs.replit.com/replitai/skills
- Replit skill customization: https://replit.com/blog/custom-skills
- Google JavaScript SEO basics: https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics
- Google canonicalization: https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls
- Google sitemap guidance: https://developers.google.com/search/docs/crawling-indexing/sitemaps/overview
- Google structured data policies: https://developers.google.com/search/docs/appearance/structured-data/sd-policies
- Web performance metrics: https://web.dev/articles/vitals
- WCAG 2.2: https://www.w3.org/TR/WCAG22/
