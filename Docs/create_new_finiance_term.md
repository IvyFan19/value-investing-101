# Financial Term Definition Guide

## Standard Term Structure

Each financial term document should follow this structure:

### 1. Title
Format: `# {Full Term Name} ({Abbreviation})`

**Example**:
```markdown
# Price-to-Earnings (P/E) Ratio
# Trailing Twelve Months (TTM) Earnings Per Share (EPS)
```

### 2. Description
Explain what the term means and why it matters. Include:
- Clear definition of the concept
- What it measures or indicates
- Interpretation guidelines (e.g., "higher value means...", "lower value suggests...")

**Example**:
```markdown
## Description
The P/E ratio measures how much investors are willing to pay for each dollar of a company's earnings.

A higher P/E suggests investors expect strong future growth; a lower P/E may indicate lower growth expectations or potential undervaluation.
```

### 3. Formula
Present the mathematical formula using LaTeX notation, followed by data source explanations.

**Format**:
```markdown
## Formula
$$\text{Term Name} = \frac{\text{Numerator}}{\text{Denominator}}$$

Data Sources:
- [Component 1](link-to-component.md): Explanation of where to find this data
- [Component 2](link-to-component.md): Explanation of where to find this data
```

**Example**:
```markdown
## Formula
$$\text{P/E} = \frac{\text{Market Price per Share}}{\text{TTM EPS}}$$

Data Sources:
- [Market Price per Share](market-price-per-share.md): Current trading price from stock exchanges
- [TTM EPS](TTM-EPS.md): Company's net income over the last 12 months divided by outstanding shares, found in financial statements
```

### 4. Example
Provide a real-world example using an actual company, showing:
- Two time periods for comparison (demonstrating change/trend)
- Actual numbers and calculations
- Step-by-step calculation
- Interpretation of the values
- Key insight or takeaway

**Format**:
```markdown
## Example: {Company Name} ({Ticker})

**{Time Period 1}:**
- Component 1: $X | Component 2: $Y | Result: Z
- Calculation: $X / $Y = Z
- Interpretation or context

**{Time Period 2}:**
- Component 1: $X | Component 2: $Y | Result: Z
- Calculation: $X / $Y = Z
- Interpretation or context

**Key Insight:** Summary of what this example teaches about the metric
```

### 5. Warren Buffett's Interpretation (Optional but Recommended)
Include Warren Buffett's perspective on the metric, with:
- His specific buying ranges or thresholds
- Key principles for using this metric
- Practical application tips
- Warning signs to watch for

**Format**:
```markdown
## Warren Buffett's {Term} Interpretation

**Buffett's {Category} Range:**
- Specific thresholds or ranges with sources
- His preferences or rules of thumb

**Key Principles:**
- Bullet points of his key insights (with sources when available)
- How he uses this metric in practice

**Practical Application:**
- Actionable tips based on Buffett's approach

**Warning Signs:** (if applicable)
- Red flags to watch for
```

### 6. Metadata
Standard metadata fields for system integration.

**Format**:
```markdown
## Metadata
- Id: {identifier}
- Category: {category}
- Subtype: {subtype}
- Units: {units}
- Decimal Points: {decimal_points}
```

---


## Metadata Field Specifications
This defines the standard format and available values for Metadata fields when creating new financial terms.

### Id (Identifier)
**Format**: `{term_name}`

**Naming Rules**:
- Use lowercase letters
- Separate words with underscores `_`


**Examples**:
- `earnings_per_share` - EPS (ratio category, no prefix)
- `ttm_earnings_per_share` - TTM EPS
- `price_book_ratio` - P/B Ratio
- `average_price_earnings_ratio` - P/E Ratio


### Category
**Available Values**:
- `income_statement` - Income Statement items
- `balance_sheet` - Balance Sheet items
- `cash_flow_statement` - Cash Flow Statement items
- `ratios` - Financial ratios (cross-statement or market-based)

**Note**: Category determines where the term appears in SUMMARY.md structure

**Category Selection Guidelines**:
- Use the **primary data source** to determine category
- If a ratio uses data from multiple statements or includes market price, use `ratios`
- If a ratio uses only balance sheet data (e.g., debt-to-equity), use `balance_sheet` with subtype `ratios`
- Examples:
  - P/E Ratio → `ratios` (uses market price + income statement)
  - P/B Ratio → `balance_sheet` (uses market price + balance sheet, but primarily balance sheet concept)
  - Debt-to-Equity → `balance_sheet` (only balance sheet data)
  - EPS → `income_statement` (derived from income statement)

### Subtype
**Available Values**:

**Income Statement Subtypes**:
- `profitability` - Profitability metrics (e.g., EPS, Net Income)
- `revenue` - Revenue metrics
- `expense` - Expense metrics

**Balance Sheet Subtypes**:
- `assets` - Asset items
- `liabilities` - Liability items
- `equity` - Equity items
- `ratios` - Pure balance sheet ratios using only balance sheet data (e.g., Debt-to-Equity, Current Ratio)

**Note**: Market-based ratios like P/B use `balance_sheet` category because book value is the core concept, even though market price is involved

**Cash Flow Statement Subtypes**:
- `operating` - Operating cash flow
- `investing` - Investing cash flow
- `financing` - Financing cash flow

**Ratios Subtypes**:
- `valuation` - Valuation ratios (e.g., P/E, P/B)
- `profitability` - Profitability ratios (e.g., ROE, ROA)
- `liquidity` - Liquidity ratios
- `efficiency` - Efficiency ratios
- `leverage` - Leverage ratios

### Units
**Available Values**:
- `currency` - Currency amount (e.g., USD, CNY)
- `currency per share` - Currency amount per share
- `ratio` - Ratio/multiple (unitless)
- `percentage` - Percentage
- `number` - Quantity (e.g., number of shares)

### Decimal Points
**Available Values**:
- `0` - Integer (e.g., total assets, total revenue)
- `2` - Two decimal places (most common, e.g., EPS, ratios)
- `4` - Four decimal places (for high-precision ratios)


