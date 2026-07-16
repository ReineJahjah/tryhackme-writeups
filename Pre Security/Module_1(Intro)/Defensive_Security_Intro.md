# Room: Defensive Security Intro
**Path:** Pre Security / Introduction to Cyber Security
**Date:** July 2026
**Difficulty:** Easy

## Objective
Learn the basics of defensive security by monitoring a live dashboard, identifying an ongoing attack, and taking containment action to stop it — playing the role of an apprentice SOC analyst during his first solo shift.


## Key Concepts
- **Defensive Security**: the practice of protecting systems by detecting, investigating, and responding to attacks before damage occurs — the opposite role from offensive security, which attacks systems to find weaknesses.
- **Monitoring Dashboards**: tools that give defenders visibility into activity happening across devices/systems, so they can distinguish normal behavior from suspicious behavior.
- **Containment**: the immediate priority once an attack is confirmed — stopping the attacker's access right now, before digging into root cause or long-term fixes.
- **Directory Brute-Forcing (from the attacker's side)**: the suspicious activity in this room was the same kind of behavior I performed myself in the previous room using `dirb` — many rapid attempts to access hidden pages. Seeing it from the defender's side made the connection clear: what looks like normal reconnaissance to an attacker shows up as a clear pattern (rapid, repeated 404s/directory attempts) on a defender's dashboard.

## Walkthrough / Steps
1. Took on the role of apprentice SOC analyst helping Joe on his first solo shift.
2. Reviewed the monitoring dashboard after it flagged unusual activity.
3. Investigated the logged activity and identified the attack: the attacker was rapidly attempting to access many hidden pages on the website — a directory brute-force/enumeration attack (same technique as `dirb` from the previous room, now seen from the defender's point of view).
4. Moved to containment stage. The dashboard offered three response options:
   - **Block the IP address** — cuts off the attacker's device entirely.
   - **Apply rate limiting** — restricts how many requests/connections can happen in a given time window, directly countering the rapid rate of the attacker's attempts.
   - **Update security rules** — tightens access control on the sensitive pages the attacker was slipping through.
5. Selected the appropriate containment action(s) to stop the attack in progress.

## What I Learned
- **Offense and defense are two sides of the same coin.** The attack I saw here (rapid attempts to find hidden pages) is exactly what I did myself with `dirb` in the previous room — understanding the attacker's technique directly helped me recognize it faster as a defender.
- **Containment comes before root-cause fixing.** In a real incident, the priority order is: stop the bleeding first (block/rate-limit/tighten rules), then investigate deeper and patch the underlying vulnerability afterward — not the other way around.
- **Rate limiting is a strong response to rapid, repeated requests specifically** — it doesn't fully block a user, but it slows down automated brute-force behavior enough to prevent it from being effective.
- **Dashboards are only useful if you know what "normal" looks like.** Spotting the attack relied on recognizing that a burst of rapid page requests is not normal user behavior — this is core to SOC analyst pattern recognition.

## Questions I still have
- In a real SOC environment, would blocking the IP alone be enough, or would the attacker just rotate IPs and require rate limiting/rules as well?
- How would this same attack look different in real log data (e.g., timestamps, request patterns) compared to this simplified dashboard?