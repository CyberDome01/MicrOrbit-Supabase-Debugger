Here's your diagnostic tool. Here's exactly what to do:
Step 1 — Open it and sign in
Enter your email + password (the ones you use on the app) and click Sign In & Test Connection.
Step 2 — It will scan every table and tell you:

Which tables exist vs. are missing
Whether SELECT/INSERT is blocked by RLS
Whether your user_profiles row has an org_id (this is almost certainly the root cause — without it, auth.user_org_id() returns NULL and every single RLS policy silently blocks everything)

Step 3 — It generates the exact fix SQL
One click copies it → you paste it into your Supabase SQL Editor → run it → done.
My best guess at the actual problem: your user_profiles row exists but org_id is NULL or the row doesn't exist at all. That kills everything silently. The tool will confirm it in seconds.
