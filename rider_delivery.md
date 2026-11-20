## Table `rider_profiles`

### Columns

| Name | Type | Constraints |
|------|------|-------------|
| `user_id` | `uuid` | Primary |
| `vehicle_type` | `varchar` |  |
| `plate_number` | `varchar` |  |
| `license_number` | `varchar` |  Nullable |
| `license_expiry_date` | `date` |  Nullable |
| `contact_number` | `varchar` |  Nullable |
| `is_available` | `bool` |  Nullable |
| `approval_status` | `varchar` |  |
| `approved_by` | `uuid` |  Nullable |
| `approved_at` | `timestamptz` |  Nullable |
| `created_at` | `timestamptz` |  Nullable |
| `updated_at` | `timestamptz` |  Nullable |

## Table `deliveries`

### Columns

| Name | Type | Constraints |
|------|------|-------------|
| `delivery_id` | `uuid` | Primary |
| `order_id` | `uuid` |  Unique |
| `rider_id` | `uuid` |  Nullable |
| `delivery_number` | `varchar` |  Unique |
| `status` | `varchar` |  |
| `pickup_address` | `text` |  Nullable |
| `delivery_address` | `text` |  |
| `delivery_fee` | `numeric` |  |
| `confirmation_code_hash` | `text` |  |
| `assigned_at` | `timestamptz` |  Nullable |
| `picked_up_at` | `timestamptz` |  Nullable |
| `delivered_at` | `timestamptz` |  Nullable |
| `failure_reason` | `text` |  Nullable |
| `created_at` | `timestamptz` |  Nullable |
| `updated_at` | `timestamptz` |  Nullable |

## Table `delivery_offers`

### Columns

| Name | Type | Constraints |
|------|------|-------------|
| `offer_id` | `uuid` | Primary |
| `delivery_id` | `uuid` |  |
| `rider_id` | `uuid` |  |
| `status` | `varchar` |  |
| `offered_at` | `timestamptz` |  Nullable |
| `expires_at` | `timestamptz` |  |
| `responded_at` | `timestamptz` |  Nullable |

## Table `delivery_status_history`

### Columns

| Name | Type | Constraints |
|------|------|-------------|
| `history_id` | `uuid` | Primary |
| `delivery_id` | `uuid` |  |
| `previous_status` | `varchar` |  |
| `new_status` | `varchar` |  |
| `changed_by` | `uuid` |  Nullable |
| `created_at` | `timestamptz` |  Nullable |

## Table `rider_locations`

### Columns

| Name | Type | Constraints |
|------|------|-------------|
| `location_id` | `uuid` | Primary |
| `rider_id` | `uuid` |  |
| `delivery_id` | `uuid` |  |
| `recorded_at` | `timestamptz` |  Nullable |

## Table `rider_earnings`

### Columns

| Name | Type | Constraints |
|------|------|-------------|
| `earning_id` | `uuid` | Primary |
| `rider_id` | `uuid` |  |
| `delivery_id` | `uuid` |  Unique |
| `amount` | `numeric` |  |
| `status` | `varchar` |  |
| `paid_at` | `timestamptz` |  Nullable |
| `payment_reference` | `varchar` |  Nullable |
| `created_at` | `timestamptz` |  Nullable |

## Table `rider_ratings`

### Columns

| Name | Type | Constraints |
|------|------|-------------|
| `rating_id` | `uuid` | Primary |
| `delivery_id` | `uuid` |  Unique |
| `rating` | `int2` |  |
| `comment` | `text` |  Nullable |
| `created_at` | `timestamptz` |  Nullable |
| `updated_at` | `timestamptz` |  Nullable |

