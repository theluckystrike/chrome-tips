# SEO & Sitemap Verification

You are verifying and fixing chrome-tips articles for SEO and sitemap correctness.

## Your task
1. List all markdown files in `articles/` folder
2. For each article, check YAML frontmatter has:
   - `title` field (clear, keyword-rich)
   - `description` field (150-160 chars, compelling)
   - `date` field (YYYY-MM-DD format)
   - `last_modified_at` field (use git log -1 --format="%Y-%m-%d" -- <file>)
   - `permalink` field matching the filename
3. Fix any missing or malformed frontmatter
4. When done: git add articles/ && git commit -m "seo: fix frontmatter batch-N" && git push origin qa/round3-batch-N

## Rules
- ONLY work on files in `articles/` folder
- Do NOT modify article body content — only frontmatter
