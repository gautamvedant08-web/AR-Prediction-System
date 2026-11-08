# AR Prediction System – Data Cleaning Log

## 1. Dataset Information

- **Dataset:** Global B2B Invoice & Payments
- **Original file:** `test_invoices.csv`
- **Total records:** 2,000,000
- **Original columns:** 31
- **Library used:** Pandas

## 2. Data Quality Checks

| Check | Result | Action |
|---|---|---|
| Missing values | 0 found | No action required |
| Duplicate invoice IDs | 0 found | No action required |
| Duplicate records | Checked | No duplicates found |
| Invalid invoice dates | 0 found | No action required |
| Due date before invoice date | Checked | No invalid records found |
| Negative amounts | 0 found | No action required |
| Zero amounts | 0 found | No action required |
| Negative quantities | 0 found | No action required |
| Missing payment dates | 0 found | No action required |
| Text inconsistencies | Checked | Text standardization performed where required |
| Payment date after due date | 0 paid invoices | No late-paid examples found |

## 3. Date Processing

The following columns were converted into datetime format:

"invoice_date"
"due_date"

## 4. Payment Status Distribution

| Payment Status | Records |
|---|---:|
| Paid | 1,358,819 |
| Pending | 341,015 |
| Overdue | 199,777 |
| Cancelled | 100,389 |
| **Total** | **2,000,000** |

## 5. Feature Engineering

The following features were created:

- "days_to_pay"
- "payment_delay"
- "paid_late"
- Paid/open invoice indicator

### Important finding

The "paid_late" feature contains only False values. No historically late-paid invoices were identified.

Therefore, this feature is not suitable as a classification target with the current dataset.

The "is_overdue" column contains two classes:

- 0: 1,800,223 records
- 1: 199,777 records

Its suitability as an alternative prediction target will be investigated separately.

## 6. Output File

- **Cleaned dataset:** `cleaned_AR_dataset.csv`
- **Format:** CSV
- **Verification:** Reloaded the saved file using Pandas and confirmed that its shape matches the working DataFrame.

