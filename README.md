# Business Financial Diagnostics Tool

An interactive Python tool that works like a **pocket financial advisor** for small businesses. It asks simple, guided questions (no accounting background needed), calculates revenue, profit, break-even, cash-flow risk and liquidity ratios, and ends with a prioritised action plan: what to fix first.

|            |                                                                              |
|------------|------------------------------------------------------------------------------|
| **Role**   | Data analyst (portfolio project)                                             |
| **Tools**  | Python 3, matplotlib, JSON (standard library otherwise)                      |
| **Input**  | Answers typed by the business owner (costs, products, staff, cash, debts)    |
| **Output** | Console report, text report, 3 charts, history file for month-over-month use |

The running example in the prompts is a coffee shop, so every question comes with a realistic sample answer.

---

## What the report tells the owner

The report answers four questions: **What** happened, **Why** it happened, **So what** it means, **Now what** to do.

| Question     | What the tool gives you                                                                                                                                  |
|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **What**     | Revenue, costs and profit/loss, break-even revenue, margins, cash-flow runway, liquidity ratios, and an overall Business Health Score (0-100)             |
| **Why**      | A breakdown per product and per supplier, showing which product carries the business, which one drags it down, and which cost takes too large a share   |
| **So what**  | A risk level (Low / Medium / High / Critical) and what-if scenarios that show how profit changes if prices, sales or product costs move                  |
| **Now what** | The "Business Doctor": a ranked to-do list, biggest estimated financial impact first, with concrete suggestions such as which product to reprice          |

---

## How it works

The tool walks the owner through the business step by step.

**1. Collects the numbers**
- Fixed monthly costs, entered one item at a time (rent, utilities, subscriptions)
- Each product: selling price, cost to make one unit, units sold per month
- Employees and employer contributions
- Suppliers, with a warning against double-counting costs already in the product data
- Cash reserve
- Optional: VAT/sales tax, card or delivery-platform fees, waste, equipment depreciation
- Liquidity snapshot: unpaid supplier invoices, short-term debts, receivables, inventory

**2. Diagnoses the business**
- Revenue, costs and profit/loss, broken down per product and per supplier
- Break-even revenue
- Cash-flow runway: how many months the reserve lasts if the current trend continues
- Gross, operating and net margin
- Bankruptcy risk score and a combined risk level
- Liquidity ratios: current ratio, quick ratio, cash ratio and working capital, each explained in plain language
- Payroll check: how many employees, and what average salary, the business can sustain
- Business Health Score, weighted from profit, margin, cash flow, break-even and risk

**3. Tests what could go wrong**
- What-if scenarios: prices +10%, sales -20%, product costs +15%

**4. Tells the owner what to do**
- **Business Doctor:** a ranked list of problems with concrete suggestions and an estimated monthly impact for each
- **Instant price simulation:** apply the suggested prices on the spot and see every number update
- Net profit after income tax, using a rate the user provides

**5. Saves the results**
- Full text report
- Break-even chart, per-product profitability chart and scenario comparison chart
- A history file, so the next run shows what improved and what got worse compared with the previous one

---

## Design decisions

- **Nothing is guessed.** Tax, VAT and fee rates are always entered by the user. The tool does not assume any country's rules.
- **Itemised input.** Entering products and suppliers one by one is more accurate than a single estimate, and it shows which product carries the business and which one drags it down.
- **Action, not just numbers.** Each problem found comes with a concrete suggestion and an estimated monthly impact.
- **Plain language.** A glossary up front and an explanation next to every ratio.
- **Input validation.** Prices and costs are checked (for example, a product that costs more than it sells for is flagged) and every list can be redone if the user made a mistake.

---

## How to run

The script is interactive (it uses `input()`), so it runs in Google Colab or any Python terminal.

**Google Colab**
1. Open [Google Colab](https://colab.research.google.com/).
2. Paste or upload `business_model_comp.py`.
3. Run it and answer the prompts.

**Locally**
```bash
git clone https://github.com/toniker10/business-financial-diagnostics-tool.git
cd business-financial-diagnostics-tool
pip install matplotlib
python business_model_comp.py
```

**Files created at the end of a run**
- `<name>_financial_report.txt`: the full report
- `<name>_history.json`: results saved for next month's comparison
- `break_even_chart.png`, `product_profitability_chart.png`, `scenario_comparison_chart.png`

---

## Limitations

- It is a simplified planning aid and relies entirely on the numbers the user types in.
- The what-if scenarios change one factor at a time and do not model customer reaction (for example, fewer sales after a price rise).
- The Health Score weights and the risk thresholds are heuristics chosen for this project, not an industry standard.
- Amounts are displayed in one currency (`$`); multi-currency support is not built yet.
- Terminal-only: there is no graphical interface.

## Possible next steps

- Multi-language prompts
- PDF export of the report
- A web or desktop interface
- Multi-currency support

---

## Disclaimer

This tool is a planning aid, not a substitute for professional accounting, tax or financial advice. Confirm important decisions with a licensed accountant or advisor in your country.

## Contributing and license

Suggestions and pull requests are welcome; open an Issue for bugs or ideas. No license has been set yet. Adding a `LICENSE` file (for example MIT) would make the usage terms clear.
