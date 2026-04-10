# Facebook's 7-friends activation story — a PM case study.

## Context - Facebook in 2004-2006

[Untitled](Facebook's%207-friends%20activation%20story%20%E2%80%94%20a%20PM%20case%20/Untitled%2033dec508b5118096a631cb4d766c8903.csv)

## **Phase 1 — The Question to Understand the Problem**

- **The Wrong Question**
    
    "Why are some users more engaged than others?" It was too vague, which lead to feature debates.
    
- **The Correction**
    
    "What did users who stayed do differently in their first 10 days that churned users did not?”
    

> This question reframing was everything for them. It shifted the analysis from *who* users are (demographics, college, device) to *what actions* they took early. It became a behavioral cohort analysis, rather than a segmentation study.
> 

## **Phase 2 — Analyzing the Data & The Insights**

- **Step 1: Split users into cohorts**
    
    Retained (still active day 30+) vs churned (gone within 2 weeks)
    
- **Step 2: Replay their first 10 days**
    
    What action did each group take? Posts, profile edits, friend requests, messages.
    
- **Step 3: Correlate behaviors with retention**
    
    Which early actions predicted coming back? Run correlation across all event types.
    
- **Step 4: Find the signal**
    
    Friend count in first 10 days had the strongest correlation with long term retention.
    

> **The findings:** Users who connected with 7 or more friends within their first 10 days were dramatically more likely to become long-term active users. Below that threshold, most churned.
> 

<aside>

### **The “magic number”**

It wasn’t a product requirement, a guaranteed cause of retention, a universal truth for all social apps or discovered in a single afternoon.

But rather,  it was: 

- A proxy for the "aha moment" — feeling the social graph come alive
- A leading indicator to optimize onboarding around
- A signal that the network effect had clicked for that user
- A north star metric for the growth team's experiments
</aside>

> *The friends you had on Facebook determined whether the product was useful or useless. 7 friends was the threshold where your feed became genuinely interesting every time you opened the app.*
> 

## Phase 3 — Project Sense & Features

The insight wasn't just intellectually interesting but it gave the team a specific, measurable target to engineer toward. The question became: *how do we get every new user to 7 friends in 10 days?*

<aside>

## **Feature 1**

***"People you may know"***

- Surfaced in feed and on profile pages
- Used mutual friends + network graph to rank suggestions
- Reduced friction to zero, one click to send request
- The most direct lever to hit 7 friends faster
</aside>

<aside>

## **Feature 2**

***Email contact importer***

- Import Gmail, Yahoo, Hotmail contacts
- Show which contacts are already on Facebook
- Batch friend request to known people instantly
- Collapsed the friend-finding funnel dramatically
</aside>

<aside>

## **Feature 3**

***Onboarding friend step***

- New users shown friend suggestions before seeing feed
- Couldn't easily skip past the friend-adding step
- Profile completion tied to adding friends
- Engineered the first 10 days deliberately
</aside>

<aside>

**PM lesson — How a problem turned into a solid Feature**

None of these features were complex to build. The hard part was the analysis that revealed *what to build*. Once the team knew the metric (friends in first 10 days), every product decision had a clear test: "does this move more users past 7 friends faster?" That's the power of a well-defined activation metric , it turns subjective product debates into measurable experiments.

</aside>

## **PM frameworks this story teaches**

<aside>

### **Cohort retention analysis**

- Segment users by behavior, not demographics
- Compare retained vs churned cohorts on early actions
- Look for leading indicators, not lagging ones
- Tool: retention curves split by behavior buckets
</aside>

<aside>

### **Magic number / activation milestone**

- Every product has one — find yours via data
- Twitter: follow 30 people. Slack: 2,000 messages sent. Dropbox: 1 file synced
- It's a proxy for value, not value itself
- Optimize onboarding to reach it faster
</aside>

<aside>

### **North star metric thinking**

- The north star is the one metric that best captures value delivered
- Facebook's: DAU / MAU ratio (daily stickiness)
- Activation metric feeds the north star
- Every team's roadmap should connect to it
</aside>

<aside>

### **Correlation ≠ causation (the nuance)**

- 7 friends was correlated, not proven causal
- It's possible that motivated users both added friends AND retained
- Facebook validated with experiments — A/B testing onboarding flows
- Always stress-test your magic number with experiments
</aside>

## How to find YOUR magic number?

### **Step 1: Define what 'retained' means for your product**

**THE QUESTION TO ANSWER FIRST:** What does it mean for a user to be genuinely *retained* in your product?

<aside>

**Retained user (examples)**

- Still active at day 30 after signup
- Used the core feature at least 3x in week 2
- Did not churn within 90 days
- Upgraded from free to paid
</aside>

<aside>

**Churned user (examples)**

- Never came back after day 3
- Signed up, never completed setup
- Logged in once, then 0 sessions in 2 weeks
- Cancelled within 30 days
</aside>

<aside>

Pick one clear definition and stick to it for the entire analysis. Changing it mid-analysis will corrupt your results.

</aside>

> For most SaaS: "active at day 30" is a solid starting definition. For social apps: "returned within 7 days" works better because the value cycle is shorter.
> 

### **Step 2: Instrument every user action in the first N days**

**What to track in the 'first N days' window:** Choose a window that matches your product's natural activation cycle. Facebook used 10 days. Slack uses 30 days. Most B2B SaaS uses 14–30 days. The window is how long a new user realistically has to find value before deciding to stay or leave.

<aside>

**Events to log for every user**

- Every feature used, with a count (not just Boolean)
- Invitations sent / team members added
- Integrations connected or files imported
- Core action completed (e.g. first API call, first post, first project)
- Sessions: how many times did they return?
- Profile / setup completion percentage
</aside>

<aside>

If you don't have tracking yet, start with Heap or Post Hog. Heap auto-captures all clicks and form submissions retroactively, so you get historical data immediately without instrumenting every event manually.

</aside>

### Step 3: **Split users into retained vs churned cohorts**

**How to create the cohorts:** 

1. Take all users who signed up in a given period (e.g. last 6 months)
2. Wait until enough time has passed to determine retention (e.g. 30+ days)
3. Tag each user retained = true/false based on your definition from Step 1
4. Now you have two groups to compare

<aside>

**Cohort A — retained**

Users still active at day 30+. These are the people your product worked for. You want to understand what they did.

</aside>

<aside>

C**ohort B — churned**

Users who left within the window. These are the people your product failed. You want to understand what they didn't do.

</aside>

<aside>

Aim for at least 200–300 users per cohort before drawing conclusions. Smaller samples produce noisy results that lead you to the wrong magic number.

</aside>

### Step 4: **Correlate early actions with retention**

**What to compare across cohorts:** For each action you tracked in Step 2, compare the average count in the retained cohort vs the churned cohort. You're looking for the biggest gap.

<aside>

The action with the biggest relative gap is your leading candidate. In this example, "collaborators invited" has a 38x gap — that's your signal to investigate further.

</aside>

<aside>

Look for actions that are *different in kind*, not just in degree. Everyone has more sessions if they're retained — that's circular. You want the early behavior that *predicts* retention before it happens.

</aside>

### Step 5: **Find the threshold — where does the curve inflect?**

**How to find the inflection point:**

- Take your top candidate action (e.g. "collaborators invited")
- Bucket users by count: 0 invited, 1 invited, 2 invited, 3+ invited...
- For each bucket, calculate day-30 retention rate
- Plot it — you're looking for where retention stops increasing sharply

### Step 6: **Validate with an experiment — don't just act on correlation**

**Why you must validate:** Motivated users might both invite collaborators AND retain, not because inviting caused retention, but because they were already engaged. You need to prove that *nudging* users toward your magic number actually moves retention.

<aside>

**Control group**

- Track day-30 retention rate
- Measure how many hit the magic number naturally
- Normal onboarding, no special nudges
</aside>

<aside>

**Treatment group**

- Onboarding redesigned to push toward magic number
- e.g. "Invite your team" as a required step
- Track day-30 retention rate
</aside>

<aside>

**What you're measuring**

- Did the treatment group hit the magic number more often?
- Did hitting the magic number actually improve day-30 retention?
- What was the lift in retention between control and treatment?
</aside>

If retention improves in the treatment group — you've validated your magic number. Now scale: redesign your entire onboarding to get every user there as fast as possible.

Run the experiment for at least 2–4 weeks and with enough users (aim for 500+ per group) before drawing conclusions. Early results are often misleading.