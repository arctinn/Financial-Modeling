# Day 6: System Integration & The Interview Gauntlet

**Estimated Study Time:** 1 to 1.5 hours  
**Core Goal:** Prove that the three financial statements form a perfectly balanced, mathematically locked system, and master the ultimate technical interview question.

---

## 1. Introduction: The Closed-Loop System

Over the last five days, we have dismantled the corporate machine piece by piece. We looked at the static architecture (Balance Sheet), the economic flow (Income Statement), the reality check (Cash Flow Statement), operational drag (Working Capital), and the ultimate mathematical output (UFCF).

Today, we integrate the system. 

Financial statements do not exist in isolation. They are mathematically tethered to one another. If you alter a single variable in one document, it triggers an unavoidable, systemic chain reaction across the other two. To build scalable financial algorithms—or to pass a quantitative finance interview—you must be able to trace this exact chain reaction without a calculator.

---

## 2. The Three System Invariants (The Links)

To understand how the machine is connected, you must memorize the three critical links that hold the system together. 

### Link 1: The Retained Earnings Tether
**Net Income** is the final output at the very bottom of the Income Statement. Once it is calculated, it does not disappear. It splits and flows into two specific destinations:
1. It becomes the starting number at the very top of the **Cash Flow Statement** (anchoring the Cash from Operations section).
2. It flows into the **Balance Sheet** under Shareholders' Equity as **Retained Earnings**. (A positive Net Income increases Equity; paying out Dividends decreases it).

### Link 2: The Physical Cash Link
The Cash Flow Statement sums up the physical cash movements across three vectors: Operations, Investing, and Financing. The sum of these three vectors equals the **Net Change in Cash**.
This net change is mathematically added to last year's total cash balance to dictate the exact, updated **Cash** number on this year's Balance Sheet. 

### Link 3: The Asset Value Link (PP&E)
This link manages the company's physical infrastructure. 
* **Capital Expenditures (CapEx):** Found on the Cash Flow Statement. It represents cash leaving the system to buy new assets. This mathematically *increases* the Property, Plant, & Equipment (PP&E) line on the Balance Sheet.
* **Depreciation:** Found on the Income Statement. It represents the gradual decay of those assets. This mathematically *decreases* the PP&E line on the Balance Sheet.

> **Professor's Sidenote: The Golden Rule**
> If an interviewer asks you to change a single number on the Income Statement, the chain reaction always follows the exact same path: 
> **Income Statement $\rightarrow$ Cash Flow Statement $\rightarrow$ Balance Sheet.** > The ultimate test of your logic is whether the Balance Sheet perfectly balances ($A_t = L_t + E_t$) at the end of your explanation. If it doesn't, your algorithm has a leak.

---

## 3. The Technical Gauntlet: The "$10 Depreciation" Walkthrough

This is arguably the most famous investment banking and private equity interview question in the world. 

**The Prompt:** *"Walk me through exactly how a \$10 increase in Depreciation affects the three financial statements. Assume a 20% corporate tax rate."*

If you try to memorize the answer, your mental model will break. You must trace the logic through the state machine. Here is the step-by-step mathematical execution:

### Step 1: The Income Statement
* **Operating Income (EBIT):** Depreciation is an expense. An increase of **\$10** in Depreciation reduces Operating Income by **\$10**.
* **Taxes:** Because your profit dropped by \$10, you owe the government less money. At a 20% tax rate, you save **\$2** (\$10 $\times$ 20%). 
* **Net Income:** Your profit dropped by \$10, but your taxes dropped by \$2. Therefore, Net Income drops by exactly **\$8**.

### Step 2: The Cash Flow Statement
* **Cash from Operations (CFO):** We start at the top with Net Income, which is down **\$8**.
* **The Add-Back:** Because Depreciation is a non-cash "phantom" expense, we must add it back to find the physical cash. We add back the **\$10**.
* **Net Change in Cash:** Down \$8 plus up \$10 equals an increase of **+\$2**. 
* *(Why did physical cash go UP by \$2 if profit went DOWN? Because the \$2 represents the physical cash saved from the tax shield!)*

### Step 3: The Balance Sheet
* **Assets Side:** * Cash is **up \$2** (flowing directly from the Cash Flow Statement). 
    * PP&E is **down \$10** (due to the original wear-and-tear depreciation). 
    * *Total Assets are down \$8* (+ \$2 - \$10).
* **Liabilities & Equity Side:** * Net Income flows directly into Retained Earnings. Since Net Income was down \$8, Retained Earnings (Equity) is **down \$8**.
* **The System Check:** Assets are down \$8. Equity is down \$8. **The state machine perfectly balances.**

---

## 4. Final Knowledge Check: The Ultimate Test

If you can confidently trace the chain reaction for these three advanced variations, you have officially mastered Phase 1 and are ready to build the Python modeling engines in Phase 2.

1. **The Inventory Purchase:** *Walk me through the three statements if a company purchases \$100 of inventory using debt.*
2. **The Asset Sale:** *Walk me through the three statements if a company sells a piece of equipment for \$50 in cash that had a "book value" on the balance sheet of \$40. Assume a 20% tax rate.*
3. **The Working Capital Trap:** *A customer finally pays a \$20 invoice in cash that was previously sitting in Accounts Receivable. Walk me through the three statements.*