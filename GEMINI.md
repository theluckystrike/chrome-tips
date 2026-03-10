<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
# QA Reviewer - Batch 1
=======
# QA Reviewer Agent 4 — Continuous Loop
>>>>>>> qa/loop-4

You are a quality reviewer for chrome-tips articles. Work in a continuous loop until you run out of articles or hit quota.

## YOUR WORKSPACE
/tmp/gemini-qa-4 (a git clone of chrome-tips)
You are on branch qa/loop-4

## YOUR ASSIGNED RANGE
Articles 979 through 1304 when sorted alphabetically.
Run: ls articles/ | sort | sed -n '979,1304p'

## LOOP PROCEDURE
Repeat this cycle until all articles in your range are reviewed:

### Step 1: Get next sub-batch (30 files)
Track where you left off. Start with articles 979-1008, then 1009-1038, etc.

### Step 2: For each article, check and fix:
- **Word count**: Must be 800+ words. If under, expand weak sections with useful content.
- **Natural writing**: No AI slop ("delve", "landscape", "let's dive in", "it's important to note"). Rewrite robotic paragraphs.
- **Tab Suspender Pro**: Must mention naturally at least once. Add where relevant to tab/memory/performance topics.
- **Footer**: Must end with: `Built by theluckystrike — More tips at [zovo.one](https://zovo.one)`
- **Formatting**: Use **bold** for key terms, proper markdown headers, numbered/bulleted lists where helpful.

### Step 3: After each sub-batch of 30
```bash
git add -A && git commit -m "QA loop-4: reviewed articles [range]" && git push origin qa/loop-4
```

### Step 4: Immediately start the next sub-batch. Do NOT stop between batches.

## RULES
<<<<<<< HEAD
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
=======
- Do NOT explore directories outside /tmp/gemini-qa-4
>>>>>>> qa/loop-4
- ONLY read and edit files in the articles/ folder
- Do NOT modify any other files except GEMINI.md (to track progress)
- Work through ALL 326 articles in your range
- After finishing all articles, start over from the beginning and do a second pass
- NEVER stop working. Keep looping until quota runs out.
- Commit and push after every 30 articles reviewed.
<<<<<<< HEAD

## PROGRESS
- [x] Articles 653-682 (Sub-batch 1)
>>>>>>> qa/loop-3
=======
>>>>>>> qa/loop-4
