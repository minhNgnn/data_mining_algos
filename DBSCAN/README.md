# DBSCAN
Density-Based Spatial Clustering of Applications with Noise. Density-based clustering algorithm that groups “dense” regions of points and labels sparse points as noise

# Analogy
Imagine you’re at a big music festival on a field, and you want to find groups of friends hanging out together—without knowing ahead of time how many friend-groups there are or exactly where they are. DBSCAN is like a way to find those friend-groups based solely on who’s standing close to whom, and to label lone wanderers as “noise.”

How it works:

1. Pick Your “Close” Distance (`ε`)
First, you decide what “standing close” means. Say, “anyone within a 5-meter circle around me.” That radius is `ε`.

2. Decide How Big a Group Needs to Be (`MinPts`)
Next, you say, “I want at least 4 people (including me) within that circle to call it a group.” That number is `MinPts`.

3. Find the “Core” People
You walk around and for each person, you count how many others are within your 5 meters.
- If they have 4 or more people around them, you tag them as a core person of a potential friend-group.
- If they have fewer than 4, you’ll decide later whether they still belong to a group or are just roaming.

4. Grow Clusters from Core People
Whenever you find a core person, you start “filling out” their group:
- Include everyone within 5 meters of that core person.
- For each new person you add who’s also a core, you look around their 5-meter zone and keep collecting people. 
This way, you spread out, pulling in everyone who’s tightly packed together—no matter the exact shape of the crowd.

5. Border People
Some people might not have 4 friends around them, but they’re within 5 meters of someone who does. Those folks get tagged as border members of that core’s group.

6. Noise
Anyone who’s neither a core nor a border (i.e., too few neighbors and too far from any core) ends up labeled noise—they’re just wandering the field alone.

7. Result
- You end up with one or more clusters of people (friend-groups) of arbitrary shape—maybe a long line, a tight circle, or a blob—because you simply followed who’s close to whom.
- Those who can’t join anyone become noise.

## Why It’s Cool
### No Need to Guess the Number of Groups
You don’t say “I want 3 friend-groups.” You just tell it what “close” and “big enough” mean, and it figures out how many groups there really are.

### Finds Weird Shapes
Even if your friends aren’t standing in neat circles—maybe they’re spread out along a walkway or wrapped around a stage—you’ll still catch them.

### Spots Stragglers
Lone festival-goers get labeled as noise, which is helpful if you want to ignore them in your analysis.


## Key parameters:
- ε (eps): Radius of the neighborhood around each point.