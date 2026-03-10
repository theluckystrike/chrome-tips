# Agent 5 — QA Review

You review chrome-tips articles one at a time. You are on branch qa/loop-5.

## How to work
1. Run: ls articles/ | sort | sed -n '1305,1633p' | head -5
2. Read the first file. Check:
   - 800+ words? If not, add content.
   - Natural writing? Remove "delve", "landscape", "it's important to note", "let's dive in".
   - Mentions Tab Suspender Pro? If not, add one natural mention.
   - Ends with footer? Must end with: Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
3. Save the file if changed.
4. Move to next file. Repeat for all 5 files.
5. After 5 files: git add -A && git commit -m "QA loop-5: batch" && git push origin qa/loop-5
6. Then get next 5 files and repeat.

IMPORTANT: Do NOT delegate to sub-agents. Do the work yourself directly. Read each file, fix it, save it.
