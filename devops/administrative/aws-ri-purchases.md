---
description: Show RI/SP purchases for a specific month
argument-hint: YYYY-MM
---

# AWS RI/SP Purchase History

Show all Reserved Instances and Savings Plans purchased in a specific month.

## Arguments
- $1: Year-Month in YYYY-MM format (e.g., 2025-12)

## Instructions

Use aws-ri-purchases skill to fetch RI/SP purchase history for the specified month from both AWS profiles (default and hub).

After running the skill, present the results in a formatted table and provide a copy-paste summary in Korean like:

```
** {month}월 RI 구매내역

RDS RI
- {reservation_id} ({instance_class}, {engine}) => ${price_per_instance} * {count} = ${total} ({start_date} ~ {end_date})
...
Elasticache RI
- {reservation_id} ({node_type}, {engine}) => ${price_per_node} * {count} = ${total} ({start_date} ~ {end_date})
...
EC2 Savings Plans
- {savings_plan_id} => ${commitment}/hr * 8760hrs = ${annual_total} ({start_date} ~ {end_date})
...
Total Price => ${grand_total}
```
