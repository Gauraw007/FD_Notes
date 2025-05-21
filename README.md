# FD_Notes
# Important Notes on Futures and Forwards Pricing

## Cost of Carry Model

This model states that under no arbitrage conditions, the forward price equals the spot price of the asset plus the cost of carrying or holding the asset until expiration.

**Formula:**
`F(0,T) = S₀ * e^(rT)`

Where:
*   **F(0,T):** Price of the forward contract at time 0 with T years to expiry
*   **S₀:** Current price of the underlying asset
*   **r:** Risk-free interest rate (continuously compounded)
*   **T:** Time to expiry of the contract (in years)

### Arbitrage Opportunities:
*   If `F(0,T) > S₀ * e^(rT)`, arbitrageurs can buy the underlying asset and sell futures to earn a riskless profit (cash and carry arbitrage).
*   If `F(0,T) < S₀ * e^(rT)`, arbitrageurs can sell the underlying asset (short sell) and buy futures to earn a riskless profit (reverse cash and carry arbitrage).

The higher forward price compensates for the cost of financing the carrying position until the maturity of the forward contract.

---

## Variations in the Fundamental Equation:

1.  **Underlying stock pays dividend yield (q):**
    The formula adjusts to account for the dividend yield, as it reduces the cost of carrying the asset.
    **Formula:** `F(0,T) = S₀ * e^((r-q)T)`

2.  **Underlying stock pays known discrete dividends (I):**
    The present value of the expected dividends is subtracted from the spot price before compounding.
    **Formula:** `F(0,T) = (S₀ - I) * e^(rT)`
    *   **I:** Present value of the dividend amount

3.  **Underlying is a foreign currency:**
    The foreign interest rate (r<sub>f</sub>) acts like a dividend yield.
    **Formula:** `F(0,T) = S₀ * e^((r - r_f)T)`

4.  **Commodities with storage costs (U):**
    Storage costs are added to the futures price.
    *   **Absolute terms:** `F(0,T) = (S₀ + U) * e^(rT)`
        *   **U:** Present value of storage costs.
    *   **Proportion of price (u):** `F(0,T) = S₀ * e^((r+u)T)`

5.  **Consumption Commodities (with convenience yield, y):**
    These commodities offer an "extra utility" to holders, so convenience yield is subtracted from the cost of carry.
    **Formula:** `F(0,T) = S₀ * e^((r+u-y)T)`

---

## Pricing vs. Valuation:

*   **Price of a forward/future contract:** This is the rate agreed upon today for a future transaction. At initiation, the theoretical value is such that no arbitrage profit can be made.
*   **Value of a forward/future contract:** This refers to the profit or loss of the contract during its life or at maturity.
    *   **At initiation:** `V₀ = 0` (theoretically)
    *   **At maturity:** `V(T) = S(T) - F(0,T)`
    *   **During the life of the contract (at time t):** `V(t) = Sₜ - F(0,T) * e^(-r(T-t))`
        *(Note: The original document had a typo for this formula; the corrected version discounting the forward price is used here as reflected in Example 4's solution methodology).*

---

## Examples and How to Solve Them

### Example 1: Futures price on dividend-paying stock (dividend yield)

**Problem:** Tata Power is trading currently at Rs. 350. It pays dividend yield at the rate of 4% p.a. What is the futures price for a four-month contract? If risk-free rate is 8% p.a.?

**Given:**
*   S₀ = 350
*   q = 4% = 0.04 p.a.
*   T = 4 months = 4/12 years
*   r = 8% = 0.08 p.a.

**Formula:** `F(0,T) = S₀ * e^((r-q)T)`

**Solution:**
`F(0, 4/12) = 350 * e^((0.08 - 0.04) * (4/12))`
`F(0, 4/12) = 350 * e^((0.04) * (1/3))`
`F(0, 4/12) = 350 * e^(0.013333)`
`F(0, 4/12) ≈ 350 * 1.01342`
`F(0, 4/12) ≈ 354.697`

---

### Example 2: Futures price on dividend-paying stock (discrete dividend amount)

**Problem:** Consider a four-month forward contract on 500 shares with share price = Rs 75/share. Dividend @ Rs 2.50 /share is expected to accrue in 3 months. Risk-free interest is = 10% per annum. What is the value of the forward contract? (Note: The question asks for "value", but the solution calculates the "futures price" F(0,T)).

**Given:**
*   Number of shares = 500
*   S₀ per share = 75, so total S₀ = 500 × 75 = 37500
*   Dividend per share = Rs 2.50
*   Dividend accrues in 3 months (t_div = 3/12 years)
*   r = 10% = 0.10 p.a.
*   T = 4 months for the contract = 4/12 years

**Steps to solve:**
1.  Calculate the total dividend amount.
2.  Calculate the present value of the dividend (I).
3.  Use the formula `F(0,T) = (S₀ - I) * e^(rT)`.

**Solution:**
1.  Total dividend amount = 500 × 2.50 = 1250
2.  Present value of dividend (I) (discount for 3 months):
    `I = 1250 * e^(-0.1 * (3/12))`
    `I = 1250 * e^(-0.025)`
    `I ≈ 1250 * 0.97531 ≈ 1219.13`
3.  Futures price:
    `F = (37500 - 1219.13) * e^((0.10) * (4/12))`
    `F = 36280.87 * e^(0.033333)`
    `F ≈ 36280.87 * 1.03396`
    `F ≈ 37509.36`

---

### Example 3: Pricing a Currency Forward

**Problem:** Suppose US interest rate is 2% p.a. and interest rate in India is 5% p.a. Exchange rate is $0.8 per INR. What is the theoretical forward price? If actual market forward rate is $0.8100 for a two-month contract, is there an opportunity for arbitrage?

**Given:**
*   US interest rate (r<sub>f</sub>) = 2% = 0.02 p.a.
*   Indian interest rate (r) = 5% = 0.05 p.a.
*   Spot exchange rate (S₀) = $0.8 per INR
*   T = 2 months = 2/12 years
*   Actual market forward rate = $0.8100

**Formula:** `F(0,T) = S₀ * e^((r - r_f)T)`

**Solution:**

**Theoretical Forward Price:**
`F(0, 2/12) = 0.8 * e^((0.05 - 0.02) * (2/12))`
`F(0, 2/12) = 0.8 * e^((0.03) * (1/6))`
`F(0, 2/12) = 0.8 * e^(0.005)`
`F(0, 2/12) ≈ 0.8 * 1.0050125`
`F(0, 2/12) ≈ 0.80401`

**Arbitrage Opportunity:**
*   Theoretical Forward Price ≈ $0.80401
*   Actual Market Forward Rate = $0.8100

Since Actual Market Forward Rate ($0.8100) > Theoretical Forward Price ($0.80401), there is an arbitrage opportunity. The market forward price for INR is too high (INR is overpriced in the forward market).

**Arbitrage Strategy (Sell INR forward, Buy INR spot with borrowed USD):**
1.  Borrow USD in the US (at 2% p.a.).
2.  Convert USD to INR at spot rate ($0.8 per INR).
3.  Invest INR in India (at 5% p.a.).
4.  Simultaneously, enter into a short forward contract to sell INR (and buy USD) at the actual market rate of $0.8100 / INR for delivery in 2 months.
5.  At maturity (2 months):
    *   Receive INR from your Indian investment.
    *   Deliver this INR against your forward contract and receive USD at $0.8100 / INR.
    *   Repay your USD loan with interest.
    *   The profit arises because the rate at which you sell INR ($0.8100) is higher than the theoretically fair rate ($0.80401), covering more than the net interest cost differential.

---

### Example 4: Valuation of a Futures Contract During its Tenure

**Problem:** A financial firm enters a one-year forward on a non-dividend-paying stock when stock price is Rs 40 and risk-free rate is 10% p.a. What is the forward price? What is the initial value of the contract? After six months, the stock price becomes Rs 45. What is the value of the contract?

**Given:**
*   Initial S₀ = 40
*   r = 10% = 0.10 p.a.
*   Initial T = 1 year
*   After six months (t = 0.5 years):
    *   Current Sₜ = 45
    *   Time remaining (T-t) = 1 year - 0.5 years = 0.5 years

**Steps to solve:**
1.  Calculate the initial forward price F(0,T).
2.  Determine the initial value of the contract V₀.
3.  Calculate the value of the contract after six months V(t).

**Solution:**

1.  **Initial Forward Price (F(0,T)):**
    `F(0,1) = S₀ * e^(rT)`
    `F(0,1) = 40 * e^((0.10) * 1)`
    `F(0,1) = 40 * e^(0.10)`
    `F(0,1) ≈ 40 * 1.10517 ≈ 44.2068`
    (The document states "Delivery price = 44.21 to be received at the maturity")

2.  **Initial Value of the Contract (V₀):**
    At initiation, the theoretical value of a forward contract is 0.
    `V₀ = 0`

3.  **Value of the Contract After Six Months (V(t)):**
    The delivery price F(0,T) is fixed at 44.2068.
    Current spot price (Sₜ) = 45
    Time remaining (T-t) = 0.5 years
    Formula: `V(t) = Sₜ - F(0,T) * e^(-r(T-t))`
    `V(t) = 45 - 44.2068 * e^(-0.1 * 0.5)`
    `V(t) = 45 - 44.2068 * e^(-0.05)`
    `V(t) ≈ 45 - 44.2068 * 0.951229`
    `V(t) ≈ 45 - 42.068`
    `V(t) ≈ 2.932`
    (The document shows `45 - 44.21 * e^(-0.1 * 0.5) = 2.95`, aligning with this approach and minor rounding differences).

---

### Example 5: Mark-to-Market Value of Futures

**Problem:** Suppose I hold a long futures position in 10000 shares of Z pharma. Two-month interest = 2% p.a. Z Pharma currently trading at 24.5.

A) What is the theoretical futures price on a 2-month contract?
B) The delivery price (Market or actual futures price) at entry = Rs 25 per share for a two-month contract. What is the value of futures at entry?
C) Stock price changes and the futures settlement price at the end of a month is Rs 27. What is the futures value?
D) If at the expiration, futures settlement price is Rs 24. What is my gain or loss?

**Given:**
*   Shares = 10000
*   r = 2% p.a. = 0.02 p.a.
*   Initial S₀ = 24.5
*   Initial T = 2 months = 2/12 years

**Solution:**

**A) Theoretical Futures Price:**
`F(0,T) = S₀ * e^(rT)`
`F(0, 2/12) = 24.5 * e^((0.02) * (2/12))`
`F(0, 2/12) = 24.5 * e^(0.003333)`
`F(0, 2/12) ≈ 24.5 * 1.003338 ≈ 24.5818`

**B) Value of Futures at Entry:**
The delivery price at entry (F_market) is given as Rs 25.
The value of a futures contract at the moment of initiation is theoretically 0, as no cash changes hands and it's an agreement for the future.
`V₀ = 0`

**C) Futures Value at End of One Month:**
*   Time elapsed (t) = 1 month = 1/12 year.
*   Time remaining (T-t) = 1 month = 1/12 year.
*   New settlement price (which we can treat as Sₜ for valuation purposes if the contract were a forward) = Rs 27.
*   Original Futures Price (F_entry) = Rs 25 (this is the price at which the position was entered)

For futures, the mark-to-market gain/loss for that day (or period) is based on the change in futures prices. If we consider the value of the *position* relative to the initial entry price:
The daily MTM would be `(New Futures Price - Old Futures Price) * Number of Shares`.
If we are asked for the *value of the existing contract as if it were a forward* based on the current spot price (the problem says "futures settlement price at the end of a month is Rs 27", let's assume this is the new Futures price F(t, T-t)):
Value of long position = (Current Futures Price - Original Futures Price) = `(F_current - F_entry)`
Value = `(27 - 25) * 10000 = 2 * 10000 = Rs 20,000` (This is the accumulated MTM gain).

If we use the forward valuation formula with Sₜ = 27 (assuming this is the spot price underlying the futures settlement price) and F(0,T) = 25 (the contract price):
`V(t) = Sₜ - F(0,T) * e^(-r(T-t))`
`V(t) = 27 - 25 * e^(-0.02 * (1/12))`
`V(t) = 27 - 25 * e^(-0.001666)`
`V(t) ≈ 27 - 25 * 0.998335`
`V(t) ≈ 27 - 24.958375`
`V(t) ≈ 2.0416` per share.
For 10000 shares: `10000 * 2.0416 ≈ Rs 20416`.
*The simpler approach for futures MTM is usually (New Futures Price - Previous Futures Price). If Rs 27 is the new futures price for settlement, and the position was entered at Rs 25, the gain is (27-25) per share.*

**D) Gain or Loss at Expiration:**
*   Futures settlement price at expiration (S<sub>T</sub>) = Rs 24
*   Original delivery price (F_entry) = Rs 25

For a long futures position, the gain/loss per share at expiration is `S_T - F_entry`.
Gain/Loss per share = `24 - 25 = -1`
Total Gain/Loss = `10000 shares * (-1 Rs/share) = -10000 Rs`.
This represents a loss of Rs 10,000.
