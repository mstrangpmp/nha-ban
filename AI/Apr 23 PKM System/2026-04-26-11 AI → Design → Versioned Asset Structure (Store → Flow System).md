**Needs: If I had a file that manages all versions and a production-ready file version to upload to other systems. How should I organize them?**

To handle version control and external portability without cluttering your system, I recommend a **"Core & History"** approach within your **99_SYSTEM** layer.

## Classification

- **Primary:** SYSTEM (F)
    
- **Secondary:** OUTPUT (E) (for the final version only)
    

## Recommended Location

- **Location A (Management & History):** `99_SYSTEM/Prompt_Library/GTP-PMP/GTP-PMP_Master.md`
    
- **Location B (Final/Exportable):** `05_OUTPUTS/Templates/GTP-PMP_Final.md`
    
- **Note type:** `system-note` (Master) and `output-note` (Final)
    

---

## Why it belongs there

- **The Master Note (System):** This is where you track changes, log previous versions, and store the "logic" of the prompt. It’s part of your PKM’s machinery.
    
- **The Final Note (Output):** By placing a clean, standalone copy in `05_OUTPUTS`, you treat it as a "finished product." This makes it easy to find when you need to upload it to a new AI tool without wading through your internal dev notes.
    

## Why it does NOT belong elsewhere

- Putting both in **Projects** is wrong because the work is done; it's now an asset.
    
- Putting them in **Inbox** is wrong because these are processed, high-value instructions.
    

---

## Project Decision

**Do not create a project.** This is a simple file-management task. Use a single note with "Version History" as a heading rather than creating a complex folder structure.

## Suggested Links

- `[[99_SYSTEM/Workflows/AI_Update_Workflow]]` (Link the master note to how you update it)
    
- `[[00_INBOX/AI/GTP-PMP/]]` (Link the master note back to the original source conversations for context)
    

---

## Minimal Next Action

1. Create `99_SYSTEM/Prompt_Library/GTP-PMP_Master.md`.
    
2. Use **Headings** for versioning: `## v1.1 (Current)`, `## v1.0 (Archive)`, and `## Change Log`.
    
3. **Copy-paste** the latest clean version into `05_OUTPUTS/Templates/` for easy external uploading.
    

---

### Suggested Workflow

**Iterate in System -> Deploy to Outputs**

- When you want to refine the instruction: Edit the **Master** in `99_SYSTEM`.
    
- Once tested and "Final": Update the copy in `05_OUTPUTS`.