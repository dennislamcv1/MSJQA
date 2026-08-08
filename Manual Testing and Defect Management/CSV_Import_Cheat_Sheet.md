# CSV Import Cheat Sheet

**MindBridge Education | Importing `MindBridge_Bugs.csv` into Jira Cloud**

Use this one-page reference while you import the bug backlog in Task 1. It explains the file, the exact import path, and how to map each column to a Jira field.

---

## What is in the file

`MindBridge_Bugs.csv` contains 10 previously discovered MindBridge bugs. It has five columns and a header row:

| Column | What it holds | Jira field to map to |
| ----- | ----- | ----- |
| Summary | The bug title (one specific sentence) | Summary (required) |
| Description | Steps, expected result, and actual result | Description |
| Priority | Highest, High, Medium, or Low | Priority |
| Component | The MindBridge area (Checkout, Search, Admin, and so on) | Component/s |
| Status | All rows are `To Do` | Status |

Every row is a **Bug**, and every row imports with the status **To Do** so you start with a clean practice backlog.

---

## The import path (Jira Cloud)

You must be a Jira **administrator** to use this importer. A free Jira Cloud account that you create yourself makes you the admin automatically.

1. Select the **gear icon** (Settings) in the top-right corner.
2. Select **System**.
3. In the left sidebar, under **Import and export**, select **External System Import**.
4. Select **CSV**.
5. Select **Choose File**, pick `MindBridge_Bugs.csv`, then select **Next**.

---

## Mapping the fields

On the setup screen:

- **Project:** select the project you want the bugs to land in (use an existing project, or create one first).
- **Issue type:** when the importer asks which issue type to use, choose **Bug**. (The file has no Issue Type column, so the importer applies the type you select to every row.)
- **Date format:** leave the default; this file has no date columns.

On the **Map fields** screen, set these mappings:

| CSV column | Map to Jira field | Also tick "Map field value"? |
| ----- | ----- | ----- |
| Summary | Summary | No |
| Description | Description | No |
| Priority | Priority | No |
| Component | Component/s | No |
| Status | Status | Optional |

Then finish the import and return to your project's backlog or board.

---

## Quick fixes for common snags

- **The importer needs the Priority or Status values to exist.** Tick **Map field value** next to that column and match each CSV value (for example, `To Do`) to the matching Jira value. Default Jira projects already include `To Do`, `High`, `Medium`, and `Low`.
- **You do not want to map Status.** Leave it unmapped. New issues default to the first workflow status, which is **To Do** — exactly what this lab needs.
- **Components do not exist yet.** The importer offers to create missing components for you; accept that, or pre-create them in **Project settings → Components**.
- **You imported but see nothing.** Jira sometimes shows: *"Jira is refreshing your work items in the background after a migration. For up to 12 hours, filters, reports, JQL, and some searches might not show every item."* This is expected and your data is safe. Open the board directly, or refresh after a short wait.

---

## Done when

- The importer reports **10 issues created**.
- Your board or backlog shows the 10 MindBridge bugs, each as a **Bug** in status **To Do**.
