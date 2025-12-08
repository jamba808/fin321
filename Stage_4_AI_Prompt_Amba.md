**\# FX Hedging Model \- Structured AI Prompt**  
**\#\# Stage 4 Deliverable 1**

You are a financial modeling assistant specializing in foreign exchange hedging strategies.

\---

**\#\# GOAL**  
Create a fully functional Excel workbook that models **\*\*forward hedges\*\***, **\*\*money market hedges\*\***, and **\*\*option hedges\*\*** for a EUR receivable scenario. The model must include sensitivity analysis, named ranges, color-coded cells, and verification of interest rate parity.

**\*\*All required values and specifications are provided in this prompt. You have everything needed to build the complete model.\*\***

\---

**\#\# STAGE 3 REFERENCE (Existing Model Structure)**

The following structure is based on the Stage 3 skeleton model. Use this as a reference for layout and formula patterns:

**\#\#\# Stage 3 Layout Summary:**  
\- **\*\*Rows 1-2\*\***: Scenario description  
\- **\*\*Rows 4-11\*\***: Input variables section (labeled "Given")  
\- **\*\*Row 13\*\***: Forward hedge calculation  
\- **\*\*Rows 15-18\*\***: Money market hedge (3 steps)  
\- **\*\*Rows 20-24\*\***: Option hedge calculations  
\- **\*\*Rows 26-29\*\***: Sensitivity analysis parameters  
\- **\*\*Rows 31-42\*\***: Sensitivity table (11 scenarios)  
\- **\*\*Rows 44-55\*\***: Effective hedge rate calculations

**\#\#\# Key Formula Patterns from Stage 3:**  
\- **\*\*Forward Hedge\*\***: \`=FC\_AMT \* F0\_in\` → Result: $4,893,750  
\- **\*\*MM Hedge Step 1\*\***: \`=FC\_AMT / (1 \+ R\_FC)\` → Borrow EUR: €4,405,286.34  
\- **\*\*MM Hedge Step 2\*\***: \`=EUR\_borrowed \* S0\_in\` → Convert: $5,128,634.36  
\- **\*\*MM Hedge Step 3\*\***: \`=USD\_today \* (1 \+ R\_USD)\` → Invest: $5,339,421.23  
\- **\*\*Option Premium\*\***: \`=FC\_AMT \* PREM\_PUT\` → Cost: $67,500  
\- **\*\*Put Payoff (ST \< K)\*\***: \`=FC\_AMT \* K\_PUT \- Premium\_FV\` → Floor: $5,238,900  
\- **\*\*Put Payoff (ST \> K)\*\***: \`=FC\_AMT \* ST \- Premium\_FV\` → Variable outcome

**\#\#\# Sensitivity Table Structure:**  
\- **\*\*Column A\*\***: Scenario number (1-11)  
\- **\*\*Column B\*\***: Future spot rates (1.11 to 1.23, stepping by 0.01-0.02)  
\- **\*\*Column C\*\***: Forward hedge results (constant $4,893,750)  
\- **\*\*Column D\*\***: MM hedge results (constant $5,339,421.23)  
\- **\*\*Column E\*\***: Option hedge results (varies by scenario)  
\- **\*\*Column F\*\***: Action ("exercise put" or "let expire")

**\*\*Your Stage 4 model should replicate this structure with the exact formulas specified below.\*\***

\---

**\#\# INPUT VARIABLES (Scenario-Specific)**

**\#\#\# Transaction Details**  
\- **\*\*FC\_AMT\*\*** \= 4,500,000 EUR (foreign currency receivable from European customer)  
\- **\*\*T\_DAYS\*\*** \= 360 days (time to maturity \- 1 year)  
\- **\*\*T\_YRS\*\*** \= 1.0 years (calculated as T\_DAYS / 360\)

**\#\#\# Market Data (as of November 2025\)**  
\- **\*\*S0\_in\*\*** \= 1.1642 USD/EUR (current EUR/USD spot rate from Yahoo Finance)  
\- **\*\*F0\_in\*\*** \= 1.0875 USD/EUR (1-year EUR/USD forward rate \- provided)  
\- **\*\*R\_USD\*\*** \= 4.11% per annum (US Dollar 1-year interest rate from Federal Reserve)  
\- **\*\*R\_FC\*\*** \= 2.15% per annum (EUR 1-year interest rate from Trading Economics)

**\#\#\# Option Parameters**  
\- **\*\*K\_PUT\*\*** \= 1.1642 USD/EUR (put option strike price \- at-the-money)  
\- **\*\*K\_CALL\*\*** \= 1.1642 USD/EUR (call option strike price \- at-the-money)  
\- **\*\*PREM\_PUT\*\*** \= 0.015 USD per EUR (put option premium per unit)  
\- **\*\*PREM\_CALL\*\*** \= 0.018 USD per EUR (call option premium per unit)

**\*\*Note\*\***: All interest rates are expressed as decimals (e.g., 4.11% \= 0.0411). Premiums are per unit of foreign currency. This scenario reflects a U.S. solar equipment importer receiving EUR payment from a European customer.

\---

**\#\# SPREADSHEET REQUIREMENTS**

**\#\#\# 1\. NAMED RANGE DEFINITIONS**  
Create the following **\*\*exact\*\*** named ranges (case-sensitive):

| Named Range | Description | Example Value |  
|-------------|-------------|---------------|  
| \`FC\_AMT\` | Foreign currency amount | 4500000 |  
| \`S0\_in\` | Spot exchange rate | 1.1642 |  
| \`F0\_in\` | Forward exchange rate | 1.0875 |  
| \`R\_USD\` | USD interest rate (decimal) | 0.0411 |  
| \`R\_FC\` | EUR interest rate (decimal) | 0.0215 |  
| \`K\_PUT\` | Put option strike | 1.1642 |  
| \`K\_CALL\` | Call option strike | 1.1642 |  
| \`PREM\_PUT\` | Put premium per unit | 0.015 |  
| \`PREM\_CALL\` | Call premium per unit | 0.018 |  
| \`T\_DAYS\` | Days to maturity | 360 |  
| \`T\_YRS\` | Years to maturity | 1.0 |

**\*\*Implementation\*\***: Use Excel's Name Manager (Formulas → Define Name) or range selection \+ name box.

**\#\#\# 2\. COLOR CODING SCHEME**  
Apply the following fill colors to all cells:

| Color | Purpose | Example Cells |  
|-------|---------|---------------|  
| **\*\*Yellow (\#FFFF00)\*\*** | Inputs / Decision Variables | S0\_in, K\_PUT, K\_CALL |  
| **\*\*Blue (\#ADD8E6)\*\*** | Assumptions / Given Data | R\_USD, R\_FC, T\_DAYS |  
| **\*\*Green (\#90EE90)\*\*** | Formulas / Calculations | PV formulas, payoffs |  
| **\*\*Gray (\#D3D3D3)\*\*** | Outputs / KPIs | Final USD receivable amounts |

**\*\*Implementation\*\***: Select cells → Home → Fill Color, or use VBA if automating.

**\#\#\# 3\. WORKSHEET STRUCTURE**  
Organize the workbook into clearly labeled sections:

**\#\#\#\# \*\*Section A: Inputs & Assumptions\*\* (Rows 1-15)**  
\- Transaction details (FC\_AMT, T\_DAYS)  
\- Market data (S0\_in, F0\_in, interest rates)  
\- Option parameters (strikes, premiums)

**\#\#\#\# \*\*Section B: Forward Hedge\*\* (Rows 17-22)**  
\- Formula: \`USD\_receivable\_forward \= FC\_AMT × F0\_in\`  
\- Display: Final USD amount under forward contract

**\#\#\#\# \*\*Section C: Money Market Hedge\*\* (Rows 24-35)**  
\- **\*\*Step 1\*\***: Borrow EUR today  
 \- Formula: \`EUR\_borrowed \= FC\_AMT / (1 \+ R\_FC × T\_YRS)\`  
\- **\*\*Step 2\*\***: Convert to USD at spot  
 \- Formula: \`USD\_today \= EUR\_borrowed × S0\_in\`  
\- **\*\*Step 3\*\***: Invest USD and calculate future value  
 \- Formula: \`USD\_future \= USD\_today × (1 \+ R\_USD × T\_YRS)\`

**\#\#\#\# \*\*Section D: Option Hedges\*\* (Rows 37-55)**  
Create **\*\*two sub-sections\*\***:

**\*\*D1. Put Option Hedge\*\***  
\- Upfront premium cost: \`Premium\_cost\_put \= FC\_AMT × PREM\_PUT\`  
\- Payoff at maturity (scenario-dependent):  
 \`\`\`  
 IF (S\_T \< K\_PUT):  
     Payoff \= FC\_AMT × K\_PUT  
 ELSE:  
     Payoff \= FC\_AMT × S\_T  
 \`\`\`  
\- Net USD receivable: \`Payoff \- Premium\_cost\_put × (1 \+ R\_USD × T\_YRS)\`

**\*\*D2. Call Option Hedge\*\*** (if selling a call to finance the put)  
\- Upfront premium received: \`Premium\_received\_call \= FC\_AMT × PREM\_CALL\`  
\- Payoff at maturity:  
 \`\`\`  
 IF (S\_T \> K\_CALL):  
     Payoff \= FC\_AMT × K\_CALL  
 ELSE:  
     Payoff \= FC\_AMT × S\_T  
 \`\`\`  
\- Net USD receivable: \`Payoff \+ Premium\_received\_call × (1 \+ R\_USD × T\_YRS)\`

**\#\#\#\# \*\*Section E: Sensitivity Analysis\*\* (Rows 57-70)**  
Create a **\*\*data table\*\*** showing net USD receivable under different future spot rates:

| Future Spot (S\_T) | Forward Hedge | MM Hedge | Put Hedge | Call Hedge |  
|-------------------|---------------|----------|-----------|------------|  
| 0.95 × S0\_in      | Formula       | Formula  | Formula   | Formula    |  
| 0.97 × S0\_in      | Formula       | Formula  | Formula   | Formula    |  
| 0.99 × S0\_in      | Formula       | Formula  | Formula   | Formula    |  
| 1.00 × S0\_in      | Formula       | Formula  | Formula   | Formula    |  
| 1.01 × S0\_in      | Formula       | Formula  | Formula   | Formula    |  
| 1.03 × S0\_in      | Formula       | Formula  | Formula   | Formula    |  
| 1.05 × S0\_in      | Formula       | Formula  | Formula   | Formula    |

**\*\*Implementation\*\***: Use Excel's Data Table feature (Data → What-If Analysis → Data Table).

\---

**\#\# MODEL LOGIC (PSEUDOCODE)**

**\#\#\# Forward Hedge**  
\`\`\`  
USD\_forward \= FC\_AMT \* F0\_in  
\`\`\`

**\#\#\# Money Market Hedge**  
\`\`\`  
1\. EUR\_borrow \= FC\_AMT / (1 \+ R\_FC \* T\_YRS)  
2\. USD\_convert \= EUR\_borrow \* S0\_in  
3\. USD\_invest \= USD\_convert \* (1 \+ R\_USD \* T\_YRS)  
\`\`\`

**\#\#\# Put Option Hedge**  
\`\`\`  
Premium\_upfront\_USD \= FC\_AMT \* PREM\_PUT \* S0\_in  
Premium\_FV \= Premium\_upfront\_USD \* (1 \+ R\_USD \* T\_YRS)

FOR each scenario S\_T:  
   IF S\_T \< K\_PUT:  
       USD\_gross \= FC\_AMT \* K\_PUT  
   ELSE:  
       USD\_gross \= FC\_AMT \* S\_T  
    
   USD\_net \= USD\_gross \- Premium\_FV  
\`\`\`

**\#\#\# Call Option Hedge (Collar Strategy)**  
\`\`\`  
Premium\_received\_USD \= FC\_AMT \* PREM\_CALL \* S0\_in  
Premium\_FV \= Premium\_received\_USD \* (1 \+ R\_USD \* T\_YRS)

FOR each scenario S\_T:  
   IF S\_T \> K\_CALL:  
       USD\_gross \= FC\_AMT \* K\_CALL  
   ELSE:  
       USD\_gross \= FC\_AMT \* S\_T  
    
   USD\_net \= USD\_gross \+ Premium\_FV  
\`\`\`

\---

**\#\# FORMATTING & VISUAL DESIGN**

**\#\#\# Cell Formatting**  
\- **\*\*Currency\*\***: Display all USD amounts with \`$\#,\#\#0.00\` format  
\- **\*\*Percentages\*\***: Display interest rates as \`0.00%\` (e.g., 5.10%)  
\- **\*\*Exchange Rates\*\***: Display as \`0.0000\` (4 decimal places)  
\- **\*\*Formulas\*\***: Show formula bar for all green cells

**\#\#\# Layout Standards**  
\- **\*\*Column Widths\*\***: Auto-fit to content (minimum 12 characters)  
\- **\*\*Row Heights\*\***: 15-18 pixels for data rows, 20 pixels for headers  
\- **\*\*Borders\*\***: Thin borders around each section, thick border around output cells  
\- **\*\*Fonts\*\***: Arial 10pt for data, Arial 11pt Bold for headers

**\#\#\# Section Headers**  
Use **\*\*merged cells\*\*** (e.g., A1:E1) with:  
\- Font: Arial 12pt Bold  
\- Fill: Dark Blue (\#00008B)  
\- Text Color: White  
\- Alignment: Center

\---

**\#\# OUTPUT REQUIREMENTS**

**\#\#\# Summary Dashboard (Top-Right)**  
Create a mini-dashboard (columns H-J, rows 2-10) showing:

| Metric | Value | Formula Reference |  
|--------|-------|-------------------|  
| **\*\*Best Case (max USD)\*\*** | \`=MAX(...)\` | Link to sensitivity table |  
| **\*\*Worst Case (min USD)\*\*** | \`=MIN(...)\` | Link to sensitivity table |  
| **\*\*Expected (at S0)\*\*** | \`=...\` | Calculate at current spot |  
| **\*\*Breakeven Rate\*\*** | \`=...\` | Where forward \= MM hedge |

**\#\#\# Key Performance Indicators**  
Display in **\*\*gray-filled cells\*\*** (outputs):  
1\. Net USD receivable for each hedge strategy  
2\. Difference vs. unhedged scenario  
3\. Cost of hedging (opportunity cost)  
4\. Protection level (% downside covered)

\---

**\#\# VERIFICATION & VALIDATION**

**\#\#\# 1\. Interest Rate Parity Check**  
Verify: **\*\*Forward Rate ≈ Spot Rate × \[(1 \+ R\_USD × T\_YRS) / (1 \+ R\_FC × T\_YRS)\]\*\***

Add a cell that calculates:  
\`\`\`  
Theoretical\_Forward \= S0\_in \* (1 \+ R\_USD \* T\_YRS) / (1 \+ R\_FC \* T\_YRS)  
Parity\_Difference \= F0\_in \- Theoretical\_Forward  
Parity\_Check \= IF(ABS(Parity\_Difference) \< 0.0010, "PASS", "FAIL")  
\`\`\`

**\#\#\# 2\. Forward-MM Hedge Equivalence**  
Verify: **\*\*USD from Forward Hedge ≈ USD from MM Hedge\*\*** (within rounding)

Add a cell:  
\`\`\`  
MM\_vs\_Forward\_Diff \= USD\_MM\_hedge \- USD\_Forward\_hedge  
Equivalence\_Check \= IF(ABS(MM\_vs\_Forward\_Diff) \< 100, "PASS", "FAIL")  
\`\`\`

**\#\#\# 3\. Named Range Audit**  
Create a **\*\*Named Ranges Checklist\*\*** (worksheet tab 2):

| Named Range | Exists? | Cell Reference | Value |  
|-------------|---------|----------------|-------|  
| FC\_AMT | \`=ISREF(FC\_AMT)\` | \`=CELL("address", FC\_AMT)\` | \`=FC\_AMT\` |  
| S0\_in | \`=ISREF(S0\_in)\` | \`=CELL("address", S0\_in)\` | \`=S0\_in\` |  
| ... | ... | ... | ... |

**\#\#\# 4\. Formula Mapping**  
Create a **\*\*Formula Documentation\*\*** sheet showing:  
\- Cell address  
\- Formula text (\`=FORMULATEXT()\`)  
\- Description  
\- Dependencies

Example:  
| Cell | Formula | Description |  
|------|---------|-------------|  
| C20 | \`=FC\_AMT\*F0\_in\` | Forward hedge USD receivable |  
| C28 | \`=FC\_AMT/(1+R\_FC\*T\_YRS)\` | EUR borrowed in MM hedge |

\---

**\#\# EXPORT & DELIVERABLES**

**\#\#\# File Requirements**  
1\. **\*\*File Name\*\***: \`FX\_Hedging\_Model\_Final.xlsx\`  
2\. **\*\*Format\*\***: Excel 2016+ (.xlsx), **\*\*not\*\*** .xls or .xlsm  
3\. **\*\*Compatibility\*\***: No macros required  
4\. **\*\*Size\*\***: Optimize for \<5MB file size

**\#\#\# Quality Checklist**  
Before export, ensure:  
\- \[ \] All named ranges defined and functional  
\- \[ \] Color coding applied per specification  
\- \[ \] Formulas calculate correctly (F9 to recalculate)  
\- \[ \] Sensitivity table updates dynamically  
\- \[ \] Verification checks return "PASS"  
\- \[ \] No \#REF\!, \#VALUE\!, or \#DIV/0\! errors  
\- \[ \] Print area set for main worksheet (fit to 1 page wide)

**\#\#\# Delivery Method**  
Provide:  
1\. **\*\*Downloadable .xlsx file\*\*** (primary deliverable)  
2\. **\*\*Formula audit log\*\*** (CSV or separate sheet)  
3\. **\*\*Brief user guide\*\*** (markdown or PDF, \<1 page)

\---

**\#\# EXECUTION INSTRUCTIONS FOR AI**

1\. **\*\*Parse all input variables\*\*** from the INPUT VARIABLES section  
2\. **\*\*Create named ranges\*\*** exactly as specified in NAMED RANGE DEFINITIONS  
3\. **\*\*Build each hedge model\*\*** following MODEL LOGIC pseudocode  
4\. **\*\*Apply color coding\*\*** per FORMATTING & VISUAL DESIGN  
5\. **\*\*Construct sensitivity table\*\*** with ±5% spot rate scenarios  
6\. **\*\*Run verification checks\*\*** and display results  
7\. **\*\*Generate formula audit\*\*** for transparency  
8\. **\*\*Export final .xlsx file\*\*** with all requirements met

\---

**\#\# EXAMPLE OUTPUT (VISUAL REFERENCE)**

\`\`\`  
┌─────────────────────────────────────────────────────────┐  
│  FX HEDGING MODEL \- EUR RECEIVABLE ANALYSIS             │  
│  U.S. Solar Equipment Importer \- European Customer      │  
├─────────────────────────────────────────────────────────┤  
│  A. INPUTS & ASSUMPTIONS                                │  
│  ┌──────────────────────┬───────────┬────────────────┐  │  
│  │ Parameter            │ Value     │ Named Range    │  │  
│  ├──────────────────────┼───────────┼────────────────┤  │  
│  │ FC Amount (EUR)      │ 4,500,000 │ FC\_AMT      \[Y\]│  │  
│  │ Spot Rate (USD/EUR)  │ 1.1642    │ S0\_in       \[Y\]│  │  
│  │ Forward Rate         │ 1.0875    │ F0\_in       \[Y\]│  │  
│  │ USD Interest Rate    │ 4.11%     │ R\_USD       \[B\]│  │  
│  │ EUR Interest Rate    │ 2.15%     │ R\_FC        \[B\]│  │  
│  │ Days to Maturity     │ 360       │ T\_DAYS      \[B\]│  │  
│  └──────────────────────┴───────────┴────────────────┘  │  
│                                                          │  
│  B. FORWARD HEDGE                                        │  
│  USD Receivable: $4,893,750 \[G\]                          │  
│                                                          │  
│  C. MONEY MARKET HEDGE                                   │  
│  Step 1 \- Borrow EUR: 4,405,286 \[G\]                     │  
│  Step 2 \- Convert USD: $5,128,632 \[G\]                   │  
│  Step 3 \- Invest USD: $5,339,501 \[G\] ← Output \[GRAY\]    │  
│                                                          │  
│  D. OPTION HEDGES                                        │  
│  Put Hedge Net USD: $5,167,200 \[G\]                      │  
│  Call Hedge Net USD: $5,153,850 \[G\]                     │  
│                                                          │  
│  E. SENSITIVITY ANALYSIS                                 │  
│  ┌────────┬─────────┬──────────┬──────────┬──────────┐  │  
│  │ S\_T    │ Forward │ MM Hedge │ Put      │ Call     │  │  
│  ├────────┼─────────┼──────────┼──────────┼──────────┤  │  
│  │ 1.1060 │ ...     │ ...      │ ...      │ ...      │  │  
│  │ ...    │ ...     │ ...      │ ...      │ ...      │  │  
│  └────────┴─────────┴──────────┴──────────┴──────────┘  │  
└─────────────────────────────────────────────────────────┘

Legend: \[Y\]=Yellow \[B\]=Blue \[G\]=Green \[GRAY\]=Output  
\`\`\`

\---

**\#\# SUCCESS CRITERIA**

This prompt is successful if the AI-generated Excel file:  
1\. ✅ Contains all 11 named ranges, correctly defined  
2\. ✅ Uses specified color coding (yellow/blue/green/gray)  
3\. ✅ Calculates forward hedge accurately  
4\. ✅ Implements 3-step money market hedge correctly  
5\. ✅ Models put and call option payoffs with premiums  
6\. ✅ Generates sensitivity table (7 scenarios, ±5% spot)  
7\. ✅ Passes parity verification check  
8\. ✅ Passes forward-MM equivalence check  
9\. ✅ Provides formula audit log  
10\. ✅ Exports as downloadable .xlsx file

This is how treasury and risk management teams use AI to accelerate model development while maintaining control and compliance.

\---

**\*\*END OF PROMPT\*\***

