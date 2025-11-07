**FX Hedging Technical Specification \- U.S. Solar Equipment Importer**

**Created by:** Jayden **Updated by:** Jayden

 **Date Created:** November 1, 2025 **Date Updated:** November 5, 2025

---

**1\. Problem Statement**

Our company expects to receive €4.5 million in one year from a European customer, exposing us to foreign exchange risk due to fluctuations in the EUR/USD exchange rate. The primary objective is to protect the USD value of this receivable against potential euro depreciation, which would reduce dollar proceeds and impact profitability and liquidity. This specification outlines a quantitative framework to evaluate and compare alternative FX hedging strategies to mitigate this risk.

---

**2\. Inputs (Known Variables)**

| Variable | Description | Unit | Example | Source |
| ----- | ----- | ----- | ----- | ----- |
| FC\_AMT | Foreign-currency receivable | EUR | 4,500,000 | Company data |
| S₀ | Current EURUSD spot rate | USD/EUR | 1.1642 | Market data |
| F₀ | 1-year EURUSD forward rate | USD/EUR | 1.0875 | Provided |
| r\_USD | USD 1-year interest rate | % | 4.11 | Market data |
| r\_EUR | EUR 1-year interest rate | % | 2.15 | Market data |
| t | Time to maturity | Years | 1 | Derived |
| K\_put | EUR Put strike | USD/EUR | 1.1642 | Analyst choice |
| K\_call Premium put Premium Call | EUR Call strike Put premium Call premium | USD/EUR USD per contract USD per contract  | 1.1642 0.015 0.018 | Analyst choice Scenario Scenario |

---

**3\. Assumptions & Constraints**

* Interest rates are quoted on a simple annual basis.  
* The forward rate corresponds to a 1-year maturity.  
* Transaction costs and credit risk are excluded.  
* Option premiums are paid upfront in USD and reduce net proceeds.  
* Exchange rates are expressed as USD per EUR.  
* Market conditions and interest rates remain stable during the analysis period.

---

**4\. Calculation Flow**

1. Calculate USD proceeds under the forward hedge by multiplying the foreign currency amount by the forward rate.  
2. Construct a synthetic forward using money market parity:  
   * Borrow EUR at the EUR interest rate.  
   * Convert EUR to USD at the spot rate.  
   * Invest USD at the USD interest rate.  
   * At maturity, repay the EUR loan and calculate net USD proceeds.  
3. Calculate USD proceeds from the option hedge:  
   * Determine payoff based on spot rate at maturity relative to the option strike.  
   * Subtract the option premium paid upfront.  
   * Calculate net USD proceeds.  
4. Perform sensitivity analysis by varying the EUR/USD spot rate ±10% and interest rates ±50 basis points.  
5. Summarize and compare USD proceeds and effective hedge rates across all strategies.

---

**5\. Outputs**

| Output | Description | Format | Purpose |
| ----- | ----- | ----- | ----- |
| USD\_Forward | USD proceeds from the forward hedge | Numeric | Certainty benchmark |
| USD\_MoneyMarket | USD proceeds from the money market hedge | Numeric | Cross-check against forward |
| USD\_Option | USD proceeds from the option hedge | Table | Sensitivity and protection |
| Effective\_Rates | Effective hedge rates for each strategy | Numeric | Comparison of cost and benefit |
| Sensitivity\_Table | Results across spot and rate scenarios | Table | Robustness check |
| Comparative\_Chart | Bar chart comparing hedge outcomes | Visual | Executive summary |

---

**6\. Sensitivity Plan**

* Vary the EUR/USD spot rate at maturity from 0.9x to 1.1x the current spot in increments.  
* Vary USD and EUR interest rates by ±50 basis points.  
* Calculate USD proceeds under each hedge for all scenarios.  
* Present results in tables and charts for clear comparison.

---

**7\. Limitations & Next Steps**

* Analysis excludes transaction costs, credit risk, and implied volatility.  
* Option premiums reduce net proceeds and must be considered.  
* A money market hedge requires liquidity and may constrain cash flow.  
* Next step: Build the Excel model implementing this specification with transparent formulas, sensitivity tables, and comparative visuals to support final recommendations.

---

**References**

Federal Reserve Bank of New York. (2025). *Effective Federal Funds Rate.* Retrieved from https://www.newyorkfed.org/markets/reference-rates/effr

Trading Economics. (2025). *Euro Area Interest Rate.* Retrieved from https://tradingeconomics.com/euro-area/interest-rate

Yahoo Finance. (2025). *EUR/USD Spot Quote.* Retrieved from [https://finance.yahoo.com/quote/EURUSD=X](https://finance.yahoo.com/quote/EURUSD=X)