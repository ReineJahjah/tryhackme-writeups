# Room: Offensive Security Intro
**Path:** Pre Security / Introduction to Cyber Security
**Date:** July 2026
**Difficulty:** Easy

## Objective
Learn the basics of offensive security by exploiting a vulnerable fake banking web application (fakebank.thm) to find hidden pages and manipulate a money transfer.

## Key Concepts
- **Offensive Security:** Proactively finding weaknesses in a system by thinking like an attacker, before real hackers do.
- **Directory Enumeration:** Many websites have hidden pages/directories not linked anywhere visible on the site, but still accessible if you know (or guess) the path.
- **IDOR / Broken Access Control:** when an app doesn't properly restrict what actions a user can perform (e.g. transferring funds without proper authorization checks).

## Commands / Tools Used
```bash
dirb http://fakebank.thm
```
- dirb: command line tool used for directory and file brute-forcing on web servers. It work by taking a wordlist and sending a request for each one to the targeted request one by one
- if server respond with valid page
(like 200 OK status) dirb flags it as found
- if page doesnt exist (404 Not Found) dirb skips it.

## What I Learned 
Hidden/unlinked pages aren't actually secure just because there's no visible link to them, this is called "security through obsecurity" and it doesnt work if the page can still be found through brute-force directory scanning. Real applications need proper authentication and authorization checks on every endpoint, not just hidden URLs.