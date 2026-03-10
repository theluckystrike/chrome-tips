<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
=======
>>>>>>> qa/loop-5
# Agent 5 — QA Review

You review chrome-tips articles one at a time. You are on branch qa/loop-5.

## How to work
1. Run: ls articles/ | sort | sed -n '1305,1633p' | head -5
<<<<<<< HEAD
=======
# Agent 1 — QA Review

You review chrome-tips articles one at a time. You are on branch qa/loop-1.

## How to work
1. Run: ls articles/ | sort | sed -n '1,326p' | head -5
>>>>>>> qa/loop-1
=======
# Agent 2 — QA Review

You review chrome-tips articles one at a time. You are on branch qa/loop-2.

## How to work
1. Run: ls articles/ | sort | sed -n '327,652p' | head -5
>>>>>>> qa/loop-2
=======
>>>>>>> qa/loop-5
2. Read the first file. Check:
   - 800+ words? If not, add content.
   - Natural writing? Remove "delve", "landscape", "it's important to note", "let's dive in".
   - Mentions Tab Suspender Pro? If not, add one natural mention.
   - Ends with footer? Must end with: Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
3. Save the file if changed.
4. Move to next file. Repeat for all 5 files.
<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
5. After 5 files: git add -A && git commit -m "QA loop-5: batch" && git push origin qa/loop-5
=======
5. After 5 files: git add -A && git commit -m "QA loop-1: batch" && git push origin qa/loop-1
>>>>>>> qa/loop-1
=======
5. After 5 files: git add -A && git commit -m "QA loop-2: batch" && git push origin qa/loop-2
>>>>>>> qa/loop-2
6. Then get next 5 files and repeat.

=======
# Agent 3 — QA Review

You review chrome-tips articles one at a time. You are on branch qa/loop-3.

## How to work
1. Run: ls articles/ | sort | sed -n '653,978p' | head -5
2. Read the first file. Check:
   - 800+ words? If not, add content.
   - Natural writing? Remove "delve", "landscape", "it's important to note", "let's dive in".
   - Mentions Tab Suspender Pro? If not, add one natural mention.
   - Ends with footer? Must end with: Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
3. Save the file if changed.
4. Move to next file. Repeat for all 5 files.
5. After 5 files: git add -A && git commit -m "QA loop-3: batch" && git push origin qa/loop-3
6. Then get next 5 files and repeat.

>>>>>>> qa/loop-3
=======
5. After 5 files: git add -A && git commit -m "QA loop-5: batch" && git push origin qa/loop-5
6. Then get next 5 files and repeat.

>>>>>>> qa/loop-5
IMPORTANT: Do NOT delegate to sub-agents. Do the work yourself directly. Read each file, fix it, save it.
