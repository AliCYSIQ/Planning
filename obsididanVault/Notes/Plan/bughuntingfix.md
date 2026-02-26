# Bug Bounty Reference — Read This Before Every Session

---

## The Core Problem You Had

- Leaving targets after 2-4 days → never getting to where bugs actually are
- Taking week-long breaks when feeling confused → confusion is the signal to push, not stop
- Picking targets randomly or by AI suggestion → no advantage, no connection, easier to quit
- This pattern repeats in everything you do → you must force yourself to stay, it takes time to fix

---

## Your Plan — Is It Good?

**Yes. Keep it.**

|Element|Status|
|---|---|
|3-2-1 hunt/study/hunt cycle|✅ Keep|
|3-4 hours minimum per day|✅ Keep|
|Reading 5 writeups + 5 reports before each session|✅ Keep|
|Studying the bug type you'll hunt that day|✅ Keep|
|Documenting ideas when you have no time to test|✅ Keep|
|Staying focused on one goal per day|✅ Keep|
|Avoiding AI over-use|✅ Keep|

**The plan was never the problem. Execution was.**

---

## How to Study (Your Method is Good — Keep It)

Your method:

> Study the bug type relevant to what you'll hunt → read writeups on it → read real reports → go apply it on your active target

**This is correct. Don't change it.**

A few additions to make it stronger:

1. **After reading a writeup** — stop and ask yourself:
    
    - How did they know to look here?
    - What assumption did the developer make that was wrong?
    - Where could this exact same logic flaw exist in MY target?
2. **Connect study directly to your target** — don't study SSRF in general. Study SSRF and then immediately think about the specific webhook or endpoint in your target that could be vulnerable.
    
3. **If you study something and can't apply it that day** — document the idea in detail (feature, why you think it's vulnerable, what to test). Come back to it on your next hunt day.
    

**Reading 5 writeups + 5 reports before sessions is strong. Keep that.**

---

## The Target-Hopping Fix

### The Timeline You're Missing

|Time on Target|What's Happening|
|---|---|
|Day 1-3|You see the surface. This is where you've been leaving.|
|Day 4-7|You start understanding how the app thinks|
|Week 2|You find edge cases, forgotten endpoints, feature interactions|
|Week 3+|You know things other hunters don't because you stayed|

**Minimum time on one target: 2 weeks. Never leave before this.**

### When You Feel Confused on a Target

❌ Do NOT take a rest week  
✅ Write down exactly what is confusing you → make that your next study session → return to the same target

Confusion means you've hit something you don't fully understand. That is exactly where bugs hide.

---

## When to Leave a Target

**Leave when:**

- You've been on it for 2+ weeks and have tested everything in scope thoroughly
- The scope is too narrow (almost nothing to test)
- You've read recent disclosed reports and the program looks dead

**Do NOT leave because:**

- You haven't found anything yet (normal in week 1)
- You feel confused (study the confusion, come back)
- It feels boring (push through it)
- A new program looks more interesting (this is the trap)

---

## How to Pick a Target (Never Random, Never AI)

**Good target has:**

1. Wide scope — subdomains, API, mobile app
2. Recently launched on the platform — less hunters, less duplicates
3. You recognize the product or understand what the business does
4. Not the one AI or top lists recommend

**How to find one:**

- Go to HackerOne or Bugcrowd
- Sort by **newest programs**
- Pick something where you understand what the company does

**Your personal connection to the app = you stay on it longer = you find bugs**

---

## How to Actually Hunt (Not Scanner Mode)

Instead of: visit site → run tools → check OWASP list → find nothing → leave  
Do this:

1. **Week 1 — Learn the app like a user**
    
    - Map every feature and endpoint
    - Read all JS files (hidden endpoints, API keys, internal logic)
    - Understand the business logic
    - Document everything even if it looks normal
2. **Week 2 — Attack with context**
    
    - Pick ONE feature per session (file upload, OAuth, webhooks, user roles, payments)
    - Think: what did the developer assume here? What happens if I break that assumption?
    - Test edge cases, test out-of-order flows, test as different user roles
    - Chain small findings into bigger ones

**Bugs live in:**

- Business logic flaws
- Forgotten/old endpoints (check JS files and old API versions)
- Features that interact with each other
- Edge cases nobody thought to test

---

## The AI Rule

Only use AI for:

- Understanding a concept you just read about
- Writing a quick helper script

Never use AI for:

- "Is this vulnerable?"
- "What should I test next?"
- Picking your target

**If you catch yourself asking AI what to test → close it, think for 10 minutes yourself first.**  
Your instinct and intuition are what find real bugs. They only grow if you use them.

---

## Before Every Session — Quick Checklist

- [ ] Read 5 writeups or reports related to what I'm hunting today
- [ ] Know which feature or bug type I'm focusing on this session
- [ ] Stay on my current target (I have not been on it for 2 weeks yet)
- [ ] If I find nothing, ask: did I check the API? JS files? Different user roles? Out-of-order flows?
- [ ] Document anything I notice, even if it doesn't seem like a bug yet
- [ ] If I feel confused — write it down, don't quit

---

## Summary in One Paragraph

Your study method is solid. Your daily/weekly plan is solid. The only thing that was broken was leaving targets too early, taking rest weeks when confused, and picking targets without intention. Fix those three things — stay on one target for a minimum of 2 weeks, push through confusion instead of resting, and pick targets based on scope and personal familiarity — and you will find bugs. You already found 2 on VDP programs with broken habits. Fix the habits and BBP follows.