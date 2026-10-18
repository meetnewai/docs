# MeetNewAI listings feed: usage examples

`GET https://meetnewai.com/api/tools.json` returns every listing (AI tools, AI games, MCP servers and agent skills) as one JSON document. No key is needed. Please cache it rather than fetching on every request. A weekly, versioned copy is kept in [meetnewai/data](https://github.com/meetnewai/data) under CC BY 4.0.

## Fetch

```bash
curl -sS https://meetnewai.com/api/tools.json -o tools.json
```

## Shape

```json
{
  "version": 1,
  "name": "MeetNewAI listings",
  "provider": "meetnewai",
  "homepage": "https://meetnewai.com",
  "count": 484,
  "generatedAt": "2026-10-18T01:58:49.751Z",
  "items": [
    {
      "slug": "perplexity",
      "name": "Perplexity",
      "kind": "product",
      "category": "ai-search",
      "categoryName": "AI research tools",
      "url": "https://perplexity.ai",
      "domain": "perplexity.ai",
      "pricing": "Price not checked yet",
      "tags": ["Research", "Search", "Citations", "Research tools"],
      "listingUrl": "https://meetnewai.com/products/perplexity",
      "listingUrlZh": "https://meetnewai.com/zh/products/perplexity",
      "verified": "2026-10-16"
    }
  ]
}
```

`count` and `generatedAt` above are from the 2026-10-18 read. `kind` is `product`, `game`, `mcp` or `skill`. `domain` is `null` when the official site lives under a path.

## Examples

```bash
# MCP servers only, name and listing URL
jq -r '.items[] | select(.kind=="mcp") | "\(.name)\t\(.listingUrl)"' tools.json

# Count listings per category
jq -r '.items[].categoryName' tools.json | sort | uniq -c | sort -rn | head

# Listings checked in the last 7 days (GNU date)
since=$(date -d '7 days ago' +%F)
jq --arg s "$since" '[.items[] | select(.verified >= $s)] | length' tools.json
```

```python
import json, urllib.request
data = json.load(urllib.request.urlopen("https://meetnewai.com/api/tools.json"))
skills = [i for i in data["items"] if i["kind"] == "skill"]
print(len(skills), "agent skills")
```
