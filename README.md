# Dada Todo List

> A task & checklist manager for Obsidian, built entirely on plain Markdown checkboxes. Your tasks live in your own notes — daily notes, an inbox note, and checklist files. No account, no cloud, no lock-in.

[简体中文](./README_zh.md) · English

---

**Dada Todo List** turns your Obsidian vault into a full-featured task and checklist manager — powered entirely by plain Markdown checkboxes (`- [ ]` / `- [x]`). No accounts, no cloud services, no proprietary database: your tasks are simply lines in your own notes, and the plugin brings them together with calendar, timeline and agenda views plus a polished editing experience.

### Who is it for?

- **Already managing tasks in Obsidian?** If your to-dos are scattered across daily notes and scattered checklists — and finding them means searching — this plugin is for you. It gathers everything you've already written into seven views (day / week / month / agenda / quadrants / checklists / list) with zero migration: your notes stay exactly where they are.
- **Haven't tried task management in Obsidian yet?** You don't need yet another to-do service. Your vault *is* your task manager: plain Markdown that stays readable forever, stored locally, synced with whatever you already use. Start with a single `- [ ]` and grow your own system from there.

### Quick start

1. Enable the core **Daily notes** plugin (Settings → Core plugins) so dated tasks land in your daily notes;
2. Click the ✅ icon in the left ribbon (or run the command "Open Dada Todo List") to open the panel;
3. Write a line `- [ ] Buy milk #life` in any daily note — it shows up in the panel instantly.

### Highlights

- **Seven views** — day timeline, seven-day week timeline with lane layout, month calendar (with Chinese lunar dates, solar terms, festivals and statutory holidays), rolling agenda, a 2×2 priority quadrants matrix, grouped checklists, and a filterable list of everything
- **Inline syntax** — write `#tags` and `[links](url)` right in the task title; they render as clickable pills and hyperlinks
- **Flexible time** — single time, time ranges (start – end), all-day, or **cross-date** (start date – end date, shown across multiple days), switchable per task
- **Subtasks** — indented lines become nested subtasks of any depth
- **Task priority** — mark tasks high / medium / low (🔺 / 🔼 / 🔽); the format is read & write compatible with the obsidian-tasks plugin, set right in the task editor
- **Tag colors** — assign a color to any tag in settings: task blocks, agenda cards and tag pills all pick it up; click the color dot in the list sidebar to change it anytime
- **Drag to reschedule** — drag tasks between days, or drag the handles on the timeline to fine-tune start / end times
- **Option/Alt + drag to copy** — hold Option (Mac) / Alt or Ctrl (Windows·Linux) while dragging to drop a copy at the target; the original stays put. In the month view the copy keeps its original times and only changes the date; on the week / day timeline the drop point becomes the new start time (original duration preserved)
- **Customizable view menu** — choose which views appear in the switcher menu and drag to reorder them; hidden views keep their order and can be restored anytime
- **Due-time reminders** — get a system notification or an in-app notice when a task comes due, with a short "da-da" chime; all-day tasks can share one fixed reminder time (e.g. 10:00). ⚠️ Desktop only: there is no background push, so nothing fires while Obsidian is closed or in the background
- **Smart extras** — overdue postponement in one click (diary tasks move into today's daily note), `Ctrl/⌘+click` to jump to the source note

### Checklist view

A checklist is a task space separate from daily notes and the inbox: each note is one checklist, ideal for shopping lists, project to-dos, reading lists, or anything that benefits from grouped tasks.

- **Two ways to identify** — a note's frontmatter `tags` include the checklist tag (default `todoList`, sub-tags included), **or** the note sits inside a folder configured under "Checklist folders" (subfolders included). Both work together — either match is enough. If you prefer not to tag your notes, folders alone can drive your checklists.
- **`###` headings are groups** — tasks are grouped by third-level headings; tasks before any heading fall into "Ungrouped". Groups can be freely added, renamed and removed.
- **List / columns layouts** — switch between the two anytime; **drag a task onto another group** to move it, or use the **+ button** beside a group heading to add a task to it.
- **Progress at a glance** — the sidebar shows live total / done counts per checklist; click a checklist name to open its note in the editor.

> ⚠️ Don't set your journal folder or the vault root (`/`) as a checklist folder: notes there would be read both as journals/inbox and as checklists, causing duplicate tasks across views.

### Installation

**Manual**: download `main.js`, `styles.css` and `manifest.json` into
`your-vault/.obsidian/plugins/dada-todo-list/`, then enable the plugin in Settings → Community plugins.

**BRAT**: install [BRAT](https://github.com/TfTHacker/obsidian42-brat) and add this repository.

### Where your data lives

| Data | Location |
|---|---|
| Dated tasks | Your **core Daily notes** folder (follows its folder & date format) — tasks are checkboxes inside each daily note |
| Dateless tasks (inbox) | `DadaTodoList.md` in the vault root by default; configurable, created automatically |
| Checklists | Any note whose frontmatter `tags` include a checklist tag (default `todoList`, configurable), **or** any note inside a folder configured under "Checklist folders" (subfolders included); either match counts, anywhere in the vault |

Everything is plain Markdown. Uninstalling the plugin changes nothing — your notes stay as they are.

### Writing checklists

A note becomes a checklist in either of two ways: its frontmatter `tags` include the checklist tag (default `todoList`), or it sits inside a folder configured under "Checklist folders" (subfolders included). Use **`###` third-level headings as group separators** — the checklist view renders one group per heading:

```markdown
---
tags:
  - todoList
---

### Work
- [ ] Finish the quarterly report #work
    - [ ] Collect data
- [x] Reply to client emails

### Life
- [ ] Book a dentist appointment
```

- **`###` heading = group name**, freely added/renamed/removed; tasks before any heading fall into "Ungrouped"
- **Indented checkboxes are subtasks**, nesting to any depth
- Switch between **list / columns** layouts; **drag a task onto another group** to move it
- Each group has a **+ button** to add tasks; the sidebar shows live total / done progress per checklist

### Data access disclosure

- **File enumeration**: the plugin lists Markdown file paths and their frontmatter to discover daily notes and checklist files (checklists are identified by their tags or by the folder they're in). Only matched daily notes (within the configured load window), the inbox file, and matched checklist files are actually read — no other file's content is ever touched.
- **localStorage**: stores only non-essential UI preferences (current view, filters, onboarding state) on the local device. It never contains note content and is never synced; it is deliberately *not* written to `data.json` to avoid triggering cloud-sync services on every interaction.

### Settings

| Option | Description |
|---|---|
| Open location | Left sidebar / main workspace tab / right sidebar |
| Language | Follow system / 简体中文 / 繁體中文 / English; the main interface updates immediately after switching, no restart needed |
| Theme color scheme | Color scheme for task blocks in the timeline, calendar and other views: Default / Morandi / Jelly / Spring / Summer greens / Autumn / Winter; color derived from the task title |
| Show lunar calendar & holidays | Lunar dates, solar terms and holiday badges in day / week / month views; turn off for Gregorian only |
| Journal folder | Folder holding your journals (dated tasks); the plugin scans it and subfolders for notes whose filename contains a date; default `/` means the vault root |
| Journal load window | Load only the last N days of journals (30 / 90 / 180 / 365 / all; default all) — lower it on large vaults for better performance |
| Inbox file | Where dateless tasks are stored (path relative to vault root); changing it offers to migrate existing tasks |
| Checklist file tag(s) | Notes whose frontmatter `tags` include any of these (or a sub-tag) become checklist files; multiple allowed |
| Checklist folders | Every note inside these folders (subfolders included) becomes a checklist file; multiple allowed, works alongside tags — either match counts. ⚠️ Don't use your journal folder or the vault root `/`, or tasks will duplicate across views |
| Week starts on | First column of the week view and month calendar; Sunday through Saturday, default Monday |
| Timeline display range | Start and end hours of the timeline view (0:00 – 24:00) to focus on the hours you use |
| View menu | Choose which views show in the switcher menu; drag rows to reorder — all views shown in default order by default |
| Add completion date marker when completing a task | Appends the completion date to the end of the task line when you check it off (e.g. ✅ 2026-10-06). On by default; turn off to skip the marker while keeping start / due date tags |
| Notify when tasks are due | Remind you with a notification plus a short sound when a task comes due. Off by default. ⚠️ Desktop only, no background push |
| Remind all-day tasks | All-day tasks have no time of day; turn on to remind them at the time below. Off by default |
| All-day reminder time | Every all-day task of the day is reminded at this time, e.g. 10:00 |
| Notification channel | System notification (desktop popup) or in-app notice; falls back to in-app when system permission is missing |

### Interface

- **Multiple languages** — follows Obsidian's interface language by default, or set manually to 简体中文 / 繁體中文 / English in settings
- **Lunar calendar** — lunar dates, solar terms and festivals in month / week view headers, available in English too
- **Theme aware** — all colors use Obsidian's native variables, adapting to light / dark and custom accents

### Language

The interface follows Obsidian's language by default; you can also set it manually under Settings → Language (Follow system / 简体中文 / 繁體中文 / English). The main interface updates immediately after switching, no restart needed.

---

## 💖 Support the author

If this plugin helps you, feel free to buy me a coffee — it keeps me motivated to keep improving it~ You can also find me on [Xiaohongshu](https://xhslink.cn/o/2G9OTVU76WP) for tips and updates.

WeChat Pay

<img src="docs/donate-wechat.jpg" alt="WeChat donation QR" width="300">

Alipay

<img src="docs/donate-alipay.jpg" alt="Alipay donation QR" width="300">

---

## 🛠 Development

```bash
npm install
npm run build     # production build (outputs: dada-todo-list/main.js, styles.css, manifest.json)
npm run dev       # dev mode: rebuild automatically on src/ changes
```

Local debugging: symlink your test vault's plugin folder to the build output (folder name must match the plugin id):

```bash
ln -s "$(pwd)/dada-todo-list" "your-vault/.obsidian/plugins/dada-todo-list"
```

## 📄 License

MIT
