# How to Pay Technical Debt Without Freezing Features

## The "Refactor Sprint" Lie
Never ask product managers or stakeholders for a "2-week refactoring sprint". You will rarely get it, and even if you do, it never fixes the root cause.
- Technical debt isn't a loan you repay in one lump sum; it's operational friction you manage continuously.
- We use the Boy Scout Rule: leave every file slightly cleaner than you found it. Add that missing index, update the Zod schema, or remove the dead utility function while working on a related business feature.

## Quantifying Tech Debt in Business Terms
Engineers lose arguments because they say "this code is ugly and poorly architected."
- Business leaders care about risk and velocity, not aesthetic code elegance.
- Say instead: "Because our database layer has no transactional boundaries here, we risk duplicate billing entries on network timeouts, which costs support 5 hours a week." Speak in terms of time, money, and release confidence.
