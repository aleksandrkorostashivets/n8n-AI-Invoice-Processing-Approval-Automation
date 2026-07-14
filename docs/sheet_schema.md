# Google Sheets Schema

Create one spreadsheet and add the following sheets. Column names are case-sensitive because n8n mappings reference them directly.

## `Invoices`

```text
invoice_id
processing_id
status
received_at
email_message_id
sender_email
file_name
vendor_name
vendor_id
invoice_number
invoice_date
due_date
currency
total_amount
iban
vendor_found
bank_details_match
is_duplicate
validation_result
risk_flags
manager_id
approval_decision
approval_comment
processed_at
drive_file_url
```

`processing_id` is the technical matching key for update operations. `invoice_id` is the business duplicate key after extraction.

## `Vendors`

```text
vendor_id
vendor_name
vendor_tax_id
contact_email
iban
default_currency
manager_id
is_active
```

## `Approval_Matrix`

```text
rule_id
currency
min_amount
max_amount
manager_id
is_active
```

Rules should not overlap for the same currency and active amount range.

## `Accounting_Export`

```text
accounting_entry_id
invoice_id
processing_id
vendor_id
vendor_name
invoice_number
invoice_date
due_date
currency
total_amount
iban
risk_flags
approval_status
approval_comment
approved_by
approved_at
drive_file_url
exported_at
```

`accounting_entry_id` is used by `Append or Update Row` to prevent repeated exports.

## `Processing_Log`

```text
error_id
occurred_at
workflow_id
workflow_name
execution_id
execution_url
execution_mode
last_node
error_message
processing_id
email_message_id
severity
error_status
```
