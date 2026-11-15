# 📊 Technical & Architectural Summary (`SUMMARY.md`)

## 1. Project Overview
The **Personal Expense & Budget Manager** is a standalone, single-file desktop application built in Python. It combines `tkinter` (`ttk`) for a responsive graphical user interface with `pandas` for tabular data aggregation, offering personal finance tracking without external database dependencies.

---

## 2. System Architecture

The application follows an event-driven, single-class Object-Oriented design (`ExpenseManagerApp`) backed by local flat-file storage:

```text
+-------------------------------------------------------------------+
|                     ExpenseManagerApp (Tkinter)                   |
|                                                                   |
|  [Budget Setup]     [Add Expense Form]     [Live Summary & Tree]  |
+---------+--------------------+-----------------------+------------+
          |                    |                       |
          v                    v                       v
  +---------------+    +---------------+      +-----------------+
  |  budget.txt   |    | expenses.csv  | <--- |  Pandas Engine  |
  | (Plain Float) |    | (Date,Cat,Amt)|      | (groupby / sum) |
  +---------------+    +---------------+      +-----------------+
```

### Key Components
* **Storage Initializer (`initialize_files`):** Runs before GUI instantiation to guarantee `expenses.csv` (with headers `Date,Category,Amount`) and `budget.txt` (defaulted to `0.0`) exist in the working directory.
* **UI Layer (`create_widgets`):** Uses the `clam` ttk theme with a slate/blue/emerald/red color palette (`#1e293b`, `#2563eb`, `#059669`, `#dc2626`), organized into:
  * **Header Banner:** Application title display.
  * **Budget Control Panel:** Input field and status readout for monthly spending limits.
  * **Expense Entry Form:** Pre-filled current date (`YYYY-MM-DD`), category `Combobox`, and amount input.
  * **Split View:** A scrollable `ttk.Treeview` table on the left paired with a read-only `tk.Text` summary widget on the right.
  * **Status Bar:** Bottom-anchored banner providing color-coded feedback for every action.

---

## 3. Core Logic & Validation

* **Input Sanitization:**
  * **Dates:** Strictly validated against `YYYY-MM-DD` via `datetime.strptime()`.
  * **Amounts & Budgets:** Parsed as `float` with bounds checking (`budget >= 0`, `amount > 0`).
* **Threshold Alert Engine:** Upon adding an expense, the app computes `pct = (total_spent / budget) * 100` and triggers tiered notifications:
  * `80% <= pct < 100%`: Warning alert indicating high budget utilization.
  * `pct == 100%`: Notification that the budget has been completely utilized.
  * `pct > 100%`: Deficit alert displaying the exact amount exceeded (`abs(remaining)`).
* **Data Aggregation (`update_summary` & `generate_report`):** Uses `pandas.read_csv()` and `df.groupby("Category")["Amount"].sum()` to dynamically recalculate category totals, overall expenditure, and remaining balance.

---

## 4. Known Limitations & Future Roadmap

1. **Cross-Platform Icon Path:** `self.icon_image` currently points to a hardcoded Windows user path (`C:\Users\adity\...`). Switching to `os.path.join(os.path.dirname(__file__), "icon.png")` will improve portability.
2. **CRUD Operations:** Currently supports *Create* and *Read*. Adding *Update* and *Delete* actions on selected `Treeview` rows would allow users to fix entry mistakes.
3. **Monthly Filtering:** All records in `expenses.csv` currently count toward the active monthly budget. Filtering by `YYYY-MM` would support multi-month historical tracking.
4. **Visual Analytics:** Integrating `matplotlib` to render a category breakdown pie/bar chart alongside the text summary.
