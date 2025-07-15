## Introduction
The DeFi Wallet Credit Scoring Model aims to assess the creditworthiness of wallets interacting with the Aave V2 protocol based on their historical transaction behavior. This project provides a scoring system that assigns a credit score between 0 and 1000 to each wallet, where higher scores indicate reliable and responsible usage, while lower scores reflect risky or exploitative behavior.

## Methodology

### Data Source
The model processes transaction-level data from the Aave V2 protocol, which includes various actions such as deposits, borrows, repays, redemptions, and liquidations. The input data is provided in a JSON format (`user-wallet-transactions.json`).

### Feature Engineering
Features are engineered at the wallet level, aggregating transaction data to create a comprehensive profile for each wallet. Key features include:

- **Activity Metrics:**
  - Total number of transactions
  - Unique days active
  - Activity span in days
  - Average transactions per day

- **Financial Behavior Metrics:**
  - Total deposit, borrow, repay, and redeem amounts in USD
  - Net deposit and borrow amounts
  - Ratios indicating borrowing and repayment behavior
  - Liquidation flags and counts

- **Asset Diversity:**
  - Number of unique assets deposited and borrowed

- **Temporal Features:**
  - Average amounts for deposits, borrows, and repays

- **Risk Indicators:**
  - Liquidation frequency
  - Borrow-repay consistency

### Scoring Logic
The scoring system is based on a rule-based approach combined with quantile-based ranking. Each wallet starts with a base score of 500, and adjustments are made based on positive and negative behaviors:

1. **Positive Adjustments:**
   - Higher scores for significant deposit volumes, consistent repayments, and long-term activity.
   - Bonuses for diverse asset interactions.

2. **Negative Adjustments:**
   - Deductions for any liquidations and high net borrow amounts.
   - Penalties for low activity or sparse transactions.

The final scores are normalized to a range of 0 to 1000 using min-max scaling.

### How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/Assignment.git
   cd Assignment
