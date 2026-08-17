# AOAL 1.9

**AOAL (An Organized Application Log), pronounced "Owl,"** is a local desktop job-application tracker built with Python 3, Tkinter, and SQLite. It keeps application records, follow-ups, clarification questions, notes, and saved documents on your own computer.

For a new installation, start with **`INITIAL_SETUP_AND_GETTING_STARTED.md`**.

## Version 1.9: Shareable Setup & Editing Update

- Added right-click **Cut, Copy, Paste, Delete, and Select All** menus to text-entry controls throughout AOAL.
- Replaced hard-coded resume choices with a local, user-managed resume list.
- Added **Manage Resumes** to the main toolbar so each user can create their own Resume Used dropdown choices without editing Python code.
- Added `job_tracker_data/resumes.txt` for portable resume-version labels.
- Added a clean distribution data folder containing a blank initialized SQLite database and attachments folder.
- Added an Initial Setup & Getting Started guide for first-time users and shared copies.
- Preserved compatibility with the AOAL 1.8 database structure.

## Existing AOAL features

- Local SQLite application database.
- Company, job title, job description, optional pay, platform, URL, location, work arrangement, employment type, and requisition ID.
- Resume and CV / cover-letter tracking.
- Recruiter contact details, status, applied date, follow-up date, and interview date/time.
- Multiple dated communication and activity notes with subjects.
- Structured clarification questions and answers linked to each application.
- Multiple named document attachments stored in the local data folder.
- Search, status filtering, platform filtering, follow-up filtering, sorting, editing, deletion, CSV import, and CSV export.
- Status colors:
  - White: ordinary or newly applied records
  - Black with white text: Rejected
  - Blue with black text: recruiter contact, screening, interview, assessment, or any record with an interview date/time
  - Green with black text: Offer or Accepted
- Searchable, editable U.S. location field with Remote, states, cities, and previously used locations.
- ZIP data backup containing the SQLite database and saved attachments.

## Starting AOAL

### macOS / Linux

```bash
chmod +x run_job_tracker.sh
./run_job_tracker.sh
```

Or:

```bash
python3 job_application_tracker.py
```

### Windows

Double-click `run_job_tracker.bat`, or run:

```bat
python job_application_tracker.py
```

## Resume choices

Click **Manage Resumes** and enter one resume name/version per line. These choices populate the Resume Used dropdown inside application records.

The resume list is stored in:

```text
job_tracker_data/resumes.txt
```

The dropdown tracks the resume name/version. To preserve the actual file submitted for a specific application, add it as a custom document in that application's Documents tab.

## Upgrading without losing existing data

AOAL stores its database, resume-choice file, and attachments in the `job_tracker_data` folder beside the Python script.

1. Close AOAL.
2. Use **Back Up Data** or copy the entire current `job_tracker_data` folder to a safe location.
3. Extract AOAL 1.9.
4. Copy your existing `job_tracker_data` folder into the new `Job_Application_Tracker` folder.
5. Launch AOAL 1.9 and verify that your records, notes, questions, resume choices, and attachments open correctly.
6. Keep the backup until the new version has been verified.

AOAL 1.9 uses the same application and clarification-question database structure as AOAL 1.8. No destructive database conversion is required.

## Follow-ups and clarification questions

Use the Follow-Up filter on the main Applications screen to show Overdue, Due Today, Upcoming, or No Date records. Click **Set Missing +7** to populate older active applications that have a valid Applied Date but no Follow-Up Date.

Open an application and select **Follow-Ups & Questions** to:

- Review or change its follow-up date
- Set Today, +3 Days, +7 Days, or Applied Date +7
- Add questions that must be clarified with the recruiter or employer
- Record confirmed answers
- Mark questions Answered or Not Needed
- Sort the question list by clicking its headings

The **Open Qs** column on the Applications screen shows the number of unanswered clarification questions for each record.

## Sorting applications

Click any column heading to sort the list. Click the same heading again to reverse the order. The active heading displays:

- `▲` for ascending order
- `▼` for descending order

Date columns are sorted as dates, ID and Open Qs are sorted numerically, and text columns are sorted alphabetically.

## Pay and notes

The pay field is optional because many postings do not disclose compensation. Leave it blank or enter **Not disclosed** rather than estimating an amount.

Communication notes are optional and should contain confirmed recruiter calls, emails, interviews, assessments, application updates, and other facts. Use Clarification Questions for information that still needs to be verified.

## Data backups

Click **Back Up Data** and choose where to save the ZIP. The backup contains the `job_tracker_data` folder, including the SQLite database, saved attachments, and resume list, plus backup information.

The database backup includes applications, dated notes, documents, follow-up dates, and clarification questions and answers.

<img width="1909" height="1091" alt="Screenshot 2026-08-16 at 20 45 19" src="https://github.com/user-attachments/assets/e03c164b-3db4-44fe-8752-8dcf9f36536a" />
<img width="1910" height="1086" alt="Screenshot 2026-08-16 at 20 45 29" src="https://github.com/user-attachments/assets/8cb1293c-b082-4e0a-9710-df385b83794a" />
<img width="1911" height="1090" alt="Screenshot 2026-08-16 at 20 45 45" src="https://github.com/user-attachments/assets/7b602a09-c917-4c77-99bf-5e92530beba6" />
<img width="1911" height="1088" alt="Screenshot 2026-08-16 at 20 45 57" src="https://github.com/user-attachments/assets/198555f9-fbeb-4737-9776-8d363db3351e" />
<img width="1908" height="1088" alt="Screenshot 2026-08-16 at 20 46 16" src="https://github.com/user-attachments/assets/d0222ff7-1b0d-440e-b8e5-2a79b1bbdd61" />
<img width="886" height="483" alt="Screenshot 2026-08-16 at 20 57 25" src="https://github.com/user-attachments/assets/b514a5f5-af31-4870-9c08-e8efb6bbc44b" />

## CSV import and export

CSV import requires nonblank `company` and `job_title` fields. Rows missing either field are skipped and reported. Active imported records with a valid Applied Date and no Follow-Up Date receive the seven-day default.

CSV export creates a spreadsheet-compatible copy of the main application table and includes readable `clarification_questions` and `clarification_answers` columns. Dated notes, attachments, and structured question records are preserved by **Back Up Data**, not by CSV round-trip import.
