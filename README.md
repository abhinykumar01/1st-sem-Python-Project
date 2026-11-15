# 💰 Personal Expense & Budget Manager

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)
![GUI](https://img.shields.io/badge/GUI-Tkinter-green)
![Pandas](https://img.shields.io/badge/Data-Pandas-150458?logo=pandas&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

A clean, lightweight desktop application built with Python (`Tkinter` and `Pandas`) to track daily expenses, enforce monthly budget limits, and generate instant category-wise spending reports—all stored locally without requiring an internet connection or database setup.

---

## ✨ Features

- **Monthly Budget Control:** Set and update a monthly budget limit (`₹`) with persistent storage.
- **Smart Threshold Alerts:** Automatically triggers visual warnings in the status bar and pop-up dialogs when spending reaches **80%**, **100%**, or **exceeds** the budget.
- **Expense Logging & Validation:** Record expenses with date (`YYYY-MM-DD`), predefined categories (*Food, Travel, Utilities, Entertainment, Shopping, Others*), and positive amount checks.
- **Interactive Expense Table:** View all historical transactions in a scrollable table view.
- **Real-Time Category Summary:** Live breakdown of total spending per category, remaining balance, and budget utilization percentage.
- **One-Click Full Report:** Generate a concise summary pop-up of your overall financial standing.
- **Zero-Config Local Storage:** Automatically creates and manages `expenses.csv` and `budget.txt` on first launch.

---

## 📂 Project Structure

```text
personal-expense-manager/
│
├── main.py              # Main application source code (Tkinter GUI & logic)
├── expenses.csv         # Auto-generated CSV storing expense records
├── budget.txt           # Auto-generated text file storing the monthly budget
├── icon.png             # (Optional) Application window icon
└── README.md            # Project documentation
```

---

## 🛠️ Prerequisites & Installation

1. **Ensure Python 3.8+ is installed** on your system.
2. **Clone the repository:**
   ```bash
   git clone [https://github.com/yourusername/personal-expense-manager.git](https://github.com/yourusername/personal-expense-manager.git)
   cd personal-expense-manager
   ```
3. **Install the required dependency (`pandas`):**
   ```bash
   pip install pandas
   ```
   *(Note: `tkinter`, `csv`, `os`, and `datetime` come pre-installed with standard Python distributions.)*

---

## 🚀 Usage

Run the application from your terminal or command prompt:

```bash
python main.py
```

1. **Set a Budget:** Enter your monthly target in the **Budget Setup** panel and click **Set Budget**.
2. **Add an Expense:** Verify the date (defaults to today), select a category, enter the amount, and click **Add Expense**.
3. **Monitor Spending:** Check the **Category Summary & Report** panel on the right for live totals, or click **Generate Full Report** for a quick overview.

> **Note on Window Icon:** Line 32 in the script references a local Windows path (`C:\Users\adity\OneDrive\Desktop\abhiny\icon.png`). If running on another machine or OS, the app safely catches the missing file error and runs normally, or you can update the path to a relative `"icon.png"`.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to fork the repository and submit a pull request.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
