# Project Summary

A quick one page version of this project, mainly for myself when I need to talk through it in an interview or application.

## The problem

Small nonprofits, food banks especially, often track donors and volunteers in spreadsheets instead of dedicated CRM software, simply because real CRM platforms cost money they do not have. That usually means messy exports, no easy way to see who is lapsing, and no simple answer to "who are our most important supporters right now."

## What I built

An Excel workbook that takes a realistic, messy donor export and a volunteer sign up log, cleans both using visible formulas, and turns them into a dashboard a development or program team could actually use. It tracks donor giving history, flags lapsed donors automatically, shows which donors are also volunteers, and summarizes outreach activity by contact method.

## Why this dataset

I used a real, anonymized university fundraising dataset from Kaggle as the base for the donor records and outreach notes, then relabeled it for a food bank context. I generated the volunteer data myself since no public dataset pairs donor and volunteer activity for one organization. About 120 of the volunteer records are linked back to real donor IDs, to model people who both give money and give time, which is common at small nonprofits.

I chose to start from real data on purpose, rather than fully synthetic data, because real data has the kind of mess (typos, inconsistent casing, missing fields, duplicate entries) that is actually worth practicing on. Fully made up data tends to be too clean to be useful for showing cleaning skills.

## What I'd do differently

The biggest thing: I originally wrote the "lapsed donor" formula with a column reference that was off by one, so it was checking the wrong fiscal years. I caught it by spot checking individual donor records against the flag instead of trusting the aggregate count, which is a habit I want to keep. It's a good reminder that a formula returning a clean looking number does not mean the logic behind it is right.

If I were starting over, I would also build the donor ID matching for the outreach log earlier, instead of leaving it as free text names. Right now matching a contact note to a specific donor record takes a manual lookup, which is realistic but not ideal.

## Skills this shows

Data cleaning with formulas (TRIM, PROPER, VALUE, SUBSTITUTE, IFERROR), duplicate detection logic, building summary tables without manual pivot tables, basic dashboard design, and writing documentation that explains not just what a project does but why it was built that way.
