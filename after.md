# After (humanized — second pass per skill)

Caching is boring infrastructure that keeps things fast. In Next.js, it runs at a few layers: request memoization, the data cache, and the router cache. Nothing magical.

If you don't have tests, you can't tell if a cached response is correct. That sounds obvious until a stale response ships to production and nobody notices for a week. The metric to watch is not just latency — it's whether the data coming back matches reality.

Some teams disable the router cache entirely when their pages change fast enough that stale data hurts more than the extra render helps. Others keep it on but set short TTLs. Both choices are reasonable; the wrong one is pretending you don't have to choose.

A quick check: does your build pass after you change a cache key? If not, something depended on the key implicitly, which means the caching layer is doing more work than it should.

If the setup feels unfinished, that's normal. Caching is the kind of thing you add properly after something breaks, not before.
