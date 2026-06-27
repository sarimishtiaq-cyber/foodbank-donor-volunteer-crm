# Data Dictionary

A plain explanation of every column in the workbook, what it means, and where it came from. Columns marked "real (relabeled)" come from the actual Kaggle dataset, just renamed to fit a food bank. Columns marked "synthetic" were generated for this project.

## Donors table (Raw_Donors and Clean_Donors)

DonorID
Unique identifier for each donor. Real (relabeled). A handful of IDs have a "-DUP" suffix on purpose, to simulate the same person being entered twice, which happens constantly in real CRMs.

ZIP Code
Donor's ZIP code. Real.

Age
Donor's age at time of export. Real. Missing for a large share of donors, which reflects the real dataset, not a mistake.

Marital Status
Married, single, widowed, divorced, separated, or blank if unknown. Real.

Gender
Donor's recorded gender. Real.

Donor Category
One of Individual Donor, Family Donor, or Community Partner. This is derived from the original dataset's membership, alumnus, and parent flags, relabeled into categories that make sense for a food bank. Some rows in the raw tab are deliberately in all capitals to simulate inconsistent data entry.

Volunteer Engaged
Y or N. Whether the donor is also flagged as engaged or involved in the organization in some way. Real (relabeled from the original "has involvement" flag). This is separate from the actual Volunteers table, and not every donor flagged Y here will show up with logged volunteer shifts, the same way a real CRM flag does not always match actual activity logs.

Wealth Rating
An estimated giving capacity range, where known. Real. Left blank for most donors, since wealth screening data is expensive and most small nonprofits only have it for a fraction of their donor base. That is realistic, not a data quality problem to fix.

Preferred Contact Type
HOME, BUSN (business), CAMP, or OTR (other). Real. Some raw values have trailing spaces on purpose, to simulate inconsistent exports.

Email on File
Y or N, whether the organization has an email address for this donor. Real.

Consecutive Years Giving
How many years in a row the donor has given, as of the most recent fiscal year. Real.

Giving FY2021 through Giving FY2025
The dollar amount given in each fiscal year. Real, relabeled to recent years for readability. Stored as text with a dollar sign in the raw tab (like "$200"), cleaned into real numbers in the Clean_Donors tab.

Total Lifetime Giving
Total amount given across all years on record. Real.

Is Donor
Y or N, whether this person has ever made a gift. Real.

Birth Date
Donor's birth date, where known. Real. Missing for most donors, since age was usually recorded instead.

Duplicate Flag (Clean_Donors only)
Formula generated. Flags any DonorID containing "-DUP" as a likely duplicate record.

Lapsed Donor Flag (Clean_Donors only)
Formula generated. Flags a donor as lapsed if they gave in FY2023 or FY2024 but gave nothing in FY2025.

Giving Rank and Lapsed Rank (Clean_Donors only)
Helper columns used internally so the dashboard can pull "top 15 donors" and "lapsed donor list" without needing array formulas. Not meant to be read directly, they exist to make the dashboard formulas work cleanly.

## Volunteers table (Raw_Volunteers and Clean_Volunteers)

VolunteerID
Unique identifier for each volunteer. Synthetic.

LinkedDonorID
If this volunteer is also a donor, this holds their DonorID from the donors table. Synthetic link, built to connect roughly 120 volunteer records back to real donor records. Blank if the volunteer is not also a donor.

Volunteer Name
Synthetic name, randomly generated.

Shift Date
Date of a single volunteer shift. Synthetic, generated across a date range from January 2024 to mid 2026.

Role
What the volunteer did during that shift (food sorting, pantry stocking, mobile distribution driving, and similar). Synthetic. Some raw values are in all lowercase on purpose, to simulate inconsistent entry.

Location
Where the shift took place (main warehouse, downtown pantry, one of two mobile routes, or a community center site). Synthetic.

Hours
How many hours that shift lasted. Synthetic. A small number of rows have this left blank on purpose, cleaned in Clean_Volunteers by filling in the average.

Also a Donor (Clean_Volunteers only)
Formula generated. Yes or No, based on whether this volunteer record has a LinkedDonorID.

Duplicate Flag (Clean_Volunteers only)
Formula generated. Flags rows that look like an identical shift logged more than once.

## Outreach log (Raw_Outreach)

Staff Member
Name of the staff member who made the contact. Real (relabeled from the original dataset, anonymized names).

Contact Method
Email, Phone, Visit, or Letter. Real.

Date
Date of the contact. Real.

Donor/Volunteer Name
Name of the person who was contacted, as free text. Real. This does not link directly to a DonorID, since real outreach logs are often written by hand with just a name, and matching that name to a specific record is a real task, not something to fake for this project.

Notes
A short summary of what the conversation or contact was about. Real, anonymized.

Substantive Contact
Y or N, whether the contact involved a real conversation versus something like an unanswered call. Real.

Outcome
Positive or Negative, how the contact went. Real.
