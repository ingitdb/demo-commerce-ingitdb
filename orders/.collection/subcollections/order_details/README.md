# 📋 order_details

> Line items for an order — each record is one product at a given quantity and unit price.

**Subcollection of [orders](../../../../orders/)** — all line items for an order are stored together in a single
`details.json` file under each order record
(e.g. `orders/$records/ord-2024-0001/order_details/details.json`).

`record_file`:
```yaml
record_file:
  name: "details.json"
  type: "[]map[string]any"
  format: json
```

| Column | Type | Required | Constraints | Foreign Key |
|--------|------|:--------:|-------------|-------------|
| id | string | ✅ | max_length:64 | |
| product_id | string | ✅ | | [products](../../../../products/) |
| quantity | int | ✅ | min:1 | |
| unit_price | float | ✅ | min:0 | |
| currency_id | string | ✅ | | [currencies](../../../../currencies/) |
| discount_percent | float | ❌ | min:0, max:100 | |
| line_total | float | ✅ | min:0 | |

### Example Records

> The records below belong to order `ord-2024-0001`.

| id | product_id | quantity | unit_price | currency_id | discount_percent | line_total |
|----|:----------:|:--------:|:----------:|:-----------:|:----------------:|:----------:|
| line-001 | prod-001 | 1 | 799.99 | USD | | 799.99 |
| line-002 | prod-003 | 1 | 19.99 | USD | | 19.99 |
