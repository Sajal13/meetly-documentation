# Search, Time, and SEO

## Search
Initially use PostgreSQL search and indexes.

Filters:
- search
- category
- location
- city
- date
- startDate
- endDate
- priceMin
- priceMax
- sort
- page
- limit

Do not introduce Elasticsearch/OpenSearch until PostgreSQL search becomes an actual scalability/product limitation.

## Time
- Persist timestamps in UTC.
- Store event timezone separately.
- Render event times in the event's timezone where product semantics require it.
- APIs should use unambiguous ISO-8601 timestamps.

Example timezone: `Asia/Dhaka`.

Recommendation: use IANA timezone identifiers rather than numeric offsets so future DST/offset changes can be handled correctly.

## Slugs
Events require unique SEO-friendly slugs.

Example:
`/events/dhaka-tech-summit-2026`

Document:
- generation
- uniqueness
- update behavior
- canonical URL
- dynamic metadata
- OpenGraph
- structured data
- sitemap
- robots.txt
