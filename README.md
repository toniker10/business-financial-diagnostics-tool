# 📊 Business Financial Diagnostics Tool

An interactive Python tool that acts like a **pocket financial advisor** for small businesses. Through simple, guided questions — no accounting background required — it calculates revenue, profit, break-even point, cash flow risk, liquidity ratios, and gives you a personalized action plan for what to fix first.

It's built with a small business owner in mind (a coffee shop is used as the running example) who has no accounting knowledge but wants to actually understand where their money is going.

---

## ✨ What it does

The tool walks you step by step through **16 sections**:

1. **Quick glossary** — explains terms like Revenue, Fixed Costs, Break-even, Margin, etc. in plain English.
2. **Fixed monthly costs** — enter rent, utilities, subscriptions, etc., one item at a time.
3. **Products/Services** — selling price, production cost, and monthly sales volume for each product individually (not lumped into one number).
4. **Employees** — salaries and employer contributions.
5. **Suppliers** — monthly cost per supplier, so nothing gets lost in the report.
6. **Cash reserve**.
7. **Optional advanced costs** — sales tax/VAT, POS/delivery platform fees, waste/spoilage, equipment depreciation.
8. **Liquidity snapshot** — liabilities, receivables, and inventory, used to calculate liquidity ratios.
9. **Full financial results** — revenue, costs, profit/loss, broken down per product and per supplier.
10. **Break-even revenue** — how much you need to sell to stop losing money.
11. **Cash flow "death spiral" detector** — how many months your reserve would last if the current trend continued.
12. **Profit margins** — gross, operating, and net margin.
13. **Bankruptcy risk score** and a combined risk level (Low / Medium / High / Critical).
14. **Liquidity ratios** — Current Ratio, Quick Ratio, Cash Ratio, Working Capital, each explained in plain language.
15. **Scenario analysis (What-If)** — what would happen with prices +10%, sales −20%, or costs +15%.
16. **Payroll calculator** — how many employees you can actually afford and the maximum sustainable average salary.
17. **Business Health Score (0-100)** — an overall health score weighted from profit, margin, cash flow, break-even, and risk.
18. **"Business Doctor"** — a personalized, priority-ranked list of issues (biggest financial impact first), with concrete suggestions such as which product to reprice or which cost is eating too large a share of revenue.
19. **Instant price simulation** — apply the suggested price changes on the spot and immediately see how every number shifts.
20. **Income tax** — calculates net profit after tax using a rate you provide (the tool never guesses country-specific tax rules).
21. **Charts** — automatically generates a break-even chart, a per-product profitability chart, and a scenario comparison chart.
22. **Final report & save** — produces a full report and saves it to a text file.
23. **Month-over-month history** — saves the results of every run so the next time you use it, it automatically shows you what improved and what got worse compared to before.

---

## 🧠 What makes it different

- **No accounting knowledge needed.** Every question comes with a real-world example (e.g. "Cappuccino sells for $3.50").
- **Nothing is guessed.** Taxes, VAT, POS fees — everything is asked as user input instead of assuming country-specific rules.
- **Product- and supplier-level breakdowns**, not just totals — so you can see exactly which product is keeping you afloat and which one is dragging you down.
- **Action, not just numbers.** The "Business Doctor" section turns the results into a concrete, ranked to-do list with estimated financial impact.
- **Progress tracking over time** through the automatic history file.

---

## 🚀 How to run it

The script was built to run interactively in **Google Colab** or any Python terminal (it relies on keyboard input via `input()`).

**Google Colab:**
1. Open [Google Colab](https://colab.research.google.com/).
2. Upload or paste the contents of `business_model_comp.py`.
3. Hit Run and answer the prompts.

**Locally, with Python 3:**
```bash
git clone https://github.com/toniker10/business-financial-diagnostics-tool.git
cd business-financial-diagnostics-tool
pip install matplotlib
python business_model_comp.py
```

At the end of the run you'll get:
- A full report printed to the console.
- A text file with your report (`<name>_financial_report.txt`).
- A history file (`<name>_history.json`) for comparing against next month's run.
- Three charts (`break_even_chart.png`, `product_profitability_chart.png`, `scenario_comparison_chart.png`).

---

## 🛠️ Tech stack

- **Python 3** (standard library, no external frameworks apart from `matplotlib`)
- `matplotlib` for the charts
- `json` for saving history between runs
- Originally built in Google Colab, but runs locally just as well

---

## ⚠️ Disclaimer

This tool is a **simplified planning aid**, not a substitute for professional accounting, tax, or financial advice. All calculations rely entirely on the numbers you provide. For important decisions, confirm the results with a licensed accountant or financial advisor in your country.

---

## 🗺️ Possible future additions

- Multi-language support for the prompts.
- PDF export of the report.
- A graphical (web/desktop) UI instead of an interactive terminal.
- Multi-currency support.

---

## 🤝 Contributing

Pull requests and suggestions are welcome. If you find a bug or have an idea for improvement, open an Issue.

## 📄 License

No license has been set for this repository yet. If you intend to share it more broadly or accept contributions, consider adding a `LICENSE` file (e.g. MIT) to make the usage terms clear.
