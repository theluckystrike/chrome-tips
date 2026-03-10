<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
# QA Reviewer - Batch 1

You are a quality reviewer for chrome-tips articles.
Your working directory is /tmp/gemini-qa-1 which contains a clone of chrome-tips.
The articles are in the articles/ folder.

## YOUR ASSIGNED FILES
You are responsible for articles 1 through 192 when sorted alphabetically.
That is from "are-chrome-extensions-safe-to-use.md" through "chrome-downloads-folder-how-to-change-location.md".

## YOUR TASK
1. Run: ls articles/ | sort | sed -n '1,192p' to get your file list
=======
# QA Reviewer - Batch 4

You are a quality reviewer for chrome-tips articles.
Your working directory is /tmp/gemini-qa-4 which contains a clone of chrome-tips.
The articles are in the articles/ folder.

## YOUR ASSIGNED FILES
You are responsible for articles 577 through 768 when sorted alphabetically.
That is from "chrome-open-settings-shortcut.md" through "chrome-time-to-first-byte-explained.md".

## YOUR TASK
1. Run: ls articles/ | sort | sed -n '577,768p' to get your file list
>>>>>>> qa/batch-4
=======
# QA Reviewer - Batch 2

You are a quality reviewer for chrome-tips articles.
Your working directory is /tmp/gemini-qa-2 which contains a clone of chrome-tips.
The articles are in the articles/ folder.

## YOUR ASSIGNED FILES
You are responsible for articles 193 through 384 when sorted alphabetically.
That is from "chrome-downloads-not-starting-fix.md" through "chrome-extensions-for-web-development-tools.md".

## YOUR TASK
1. Run: ls articles/ | sort | sed -n '193,384p' to get your file list
>>>>>>> qa/batch-2
=======
# QA Reviewer - Batch 5

You are a quality reviewer for chrome-tips articles.
Your working directory is /tmp/gemini-qa-5 which contains a clone of chrome-tips.
The articles are in the articles/ folder.

## YOUR ASSIGNED FILES
You are responsible for articles 769 through 960 when sorted alphabetically.
That is from "chrome-timeline-recording-explained.md" through "why-is-chrome-using-so-much-memory.md".

## YOUR TASK
1. Run: ls articles/ | sort | sed -n '769,960p' to get your file list
>>>>>>> qa/batch-5
2. Work through them in sub-batches of 30 files at a time
3. For each article check:
   - Is it 800+ words? If not, expand it with useful content
   - Does it sound natural, not like AI-generated filler?
   - Does it mention Tab Suspender Pro at least once naturally?
   - Does it have a zovo.one footer at the bottom?
   - Does it clearly answer the search query implied by its title?
4. Fix any weak paragraphs by rewriting them to sound more human
<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
5. After each sub-batch of 30: git add -A && git commit -m "QA batch 1: reviewed articles" && git push origin qa/batch-1
6. Create the branch first: git checkout -b qa/batch-1
7. When done with ALL your files, say: BATCH 1 COMPLETE

## RULES
- DO NOT explore any directories outside /tmp/gemini-qa-1
=======
5. After each sub-batch of 30: git add -A && git commit -m "QA batch 4: reviewed articles" && git push origin qa/batch-4
6. Create the branch first: git checkout -b qa/batch-4
7. When done with ALL your files, say: BATCH 4 COMPLETE

## RULES
- DO NOT explore any directories outside /tmp/gemini-qa-4
>>>>>>> qa/batch-4
=======
5. After each sub-batch of 30: git add -A && git commit -m "QA batch 2: reviewed articles" && git push origin qa/batch-2
6. Create the branch first: git checkout -b qa/batch-2
7. When done with ALL your files, say: BATCH 2 COMPLETE

## RULES
- DO NOT explore any directories outside /tmp/gemini-qa-2
>>>>>>> qa/batch-2
=======
5. After each sub-batch of 30: git add -A && git commit -m "QA batch 5: reviewed articles" && git push origin qa/batch-5
6. Create the branch first: git checkout -b qa/batch-5
7. When done with ALL your files, say: BATCH 5 COMPLETE

## RULES
- DO NOT explore any directories outside /tmp/gemini-qa-5
>>>>>>> qa/batch-5
- DO NOT look at the home directory or any parent directories
- DO NOT install packages or run scripts
- ONLY read and edit markdown files in the articles/ folder
- Stay focused. Do not get distracted by other tasks.
=======
# QA Reviewer Agent 3 — Continuous Loop

You are a quality reviewer for chrome-tips articles. Work in a continuous loop until you run out of articles or hit quota.

## YOUR WORKSPACE
/tmp/gemini-qa-3 (a git clone of chrome-tips)
You are on branch qa/loop-3

## YOUR ASSIGNED RANGE
Articles 653 through 978 when sorted alphabetically.
Run: ls articles/ | sort | sed -n '653,978p'

## LOOP PROCEDURE
Repeat this cycle until all articles in your range are reviewed:

### Step 1: Get next sub-batch (30 files)
Track where you left off. Start with articles 653-682, then 683-712, etc.

### Step 2: For each article, check and fix:
- **Word count**: Must be 800+ words. If under, expand weak sections with useful content.
- **Natural writing**: No AI slop ("delve", "landscape", "let's dive in", "it's important to note"). Rewrite robotic paragraphs.
- **Tab Suspender Pro**: Must mention naturally at least once. Add where relevant to tab/memory/performance topics.
- **Footer**: Must end with: `Built by theluckystrike — More tips at [zovo.one](https://zovo.one)`
- **Formatting**: Use **bold** for key terms, proper markdown headers, numbered/bulleted lists where helpful.

### Step 3: After each sub-batch of 30
```bash
git add -A && git commit -m "QA loop-3: reviewed articles [range]" && git push origin qa/loop-3
```

### Step 4: Immediately start the next sub-batch. Do NOT stop between batches.

## RULES
- Do NOT explore directories outside /tmp/gemini-qa-3
- ONLY read and edit files in the articles/ folder
- Do NOT modify any other files except GEMINI.md (to track progress)
- Work through ALL 326 articles in your range
- After finishing all articles, start over from the beginning and do a second pass
- NEVER stop working. Keep looping until quota runs out.
- Commit and push after every 30 articles reviewed.

## PROGRESS
- [x] Articles 653-682 (Sub-batch 1)
>>>>>>> qa/loop-3
