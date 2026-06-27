# Riverbend Food Bank Donor & Volunteer CRM (Excel Project)

A small, self contained Excel project that turns a messy donor export and a volunteer sign up log into something a food bank could actually use day to day. No database, no paid CRM software, just formulas, a couple of pivot style summary tables, and a dashboard tab that answers the questions a development team would actually ask.

This started as a personal portfolio project. I work in CRM and automation (n8n, HubSpot, SFMC) and wanted something that showed the same instincts applied to a nonprofit, where the budget for "buy a real CRM" usually does not exist.

## What is actually in the file

The workbook is called `Riverbend_FoodBank_CRM.xlsx` and has 8 tabs:

1. **README** (inside the workbook itself) explains the project and points you to the dashboard if you want the short version.
2. **Raw_Donors, Raw_Volunteers, Raw_Outreach** are the source data, left untouched. On purpose, this data is messy: inconsistent capitalization, trailing spaces, a handful of duplicate records, currency stored as text like "$200" instead of a number, and a lot of real, legitimate blank fields.
3. **Clean_Donors, Clean_Volunteers** clean all of that using formulas you can see and audit (TRIM, PROPER, VALUE plus SUBSTITUTE to strip dollar signs and commas, IFERROR for blanks, COUNTIF based duplicate flags). Nothing is hardcoded or pasted in as a finished value. If the raw data changes, these tabs recalculate.
4. **Donor_Summary** breaks donors down by category, wealth rating, and year over year giving, with charts.
5. **Engagement_Dashboard** is the "so what" tab: KPI tiles, a top 15 donor list, a list of lapsed donors who need a follow up call, and a summary of outreach activity by contact method.

## Where the data came from

The donor demographics and giving history are adapted from a real, anonymized university fundraising dataset on Kaggle ("Fundraising Data" by Michael Pawlus). I relabeled the fields to fit a food bank context (donor categories, wealth ratings, giving history by year) but the underlying numbers and the messiness in them are real.

The outreach log is also from that same dataset, using the real anonymized donor contact notes, just relabeled.

The volunteer data is synthetic. There is no public dataset that pairs donors and volunteers for one organization, so I generated realistic shift and hours data and linked about 120 of those volunteer records back to existing donor IDs, to model the common situation where someone is both a donor and a volunteer.

None of this represents a real food bank's actual donors. It is a demonstration of the data work, not real personal information.

## Why it is built this way

A few choices were intentional and worth calling out, since they are the actual point of the project:

- The raw tabs are kept separate from the cleaned tabs. In a real job, you almost never get clean data, and showing the "before" next to the "after" is more honest than just showing a finished spreadsheet.
- Every cleaning step is a formula, not a manually typed value. That means someone could plug in a new donor export and the cleaned tabs, summary, and dashboard all update on their own.
- The dashboard does not just restate the raw numbers, it tries to answer real questions a small nonprofit team would ask: who are our biggest supporters, who used to give and stopped, and which outreach methods are actually working.

## How to use it

Download `Riverbend_FoodBank_CRM.xlsx` and open it in Excel (Google Sheets will open it too, but a few formulas may need to recalculate). Start on the README tab inside the file, or jump straight to Engagement_Dashboard if you want the highlights first.

## What I would do next

A few honest next steps if this were a real project instead of a portfolio piece:

- Pull the donor and volunteer data into a real BI tool (Looker Studio or Power BI) so the dashboard updates automatically instead of needing a fresh export.
- Add a proper unique ID match between the outreach log and the donor table. Right now the outreach log uses free text names, which is realistic but means a human still has to match names by hand.
- Build a simple automation (n8n or similar) that flags lapsed donors automatically and creates a follow up task, instead of just listing them in a spreadsheet.

## A note on the tools

This project was built with help from Claude (Anthropic's AI model) for the data cleaning logic, formula structure, and documentation. The dataset selection, project direction, and review of the output were done by me.
