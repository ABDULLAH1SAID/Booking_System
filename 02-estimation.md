# 📊 Booking System — Back-of-the-Envelope Estimation

> A large-scale Booking System supporting **Flight Booking, Hotel Booking, Car Rental, Activities/Local Trips, Unified Cart, Payment, Booking History, and User Accounts**.
>
> This document contains **only** capacity/scale estimation (no architecture, infra, or technology decisions). All numbers are rounded, order-of-magnitude estimates with stated assumptions.

---

## 1. Users

| Metric | Value | Reasoning |
|---|---|---|
| Registered Users | **100 million** | A large-scale global platform (flights + hotels + cars + activities) operating for several years — comparable order of magnitude to established OTAs. |
| MAU | **20 million** (20% of registered) | Travel booking is infrequent, so a large share of the registered base is dormant at any time — much lower activation than social/e-commerce apps. |
| DAU | **2 million** (10% of MAU) | DAU/MAU for travel apps is low (~10%) vs 50–60% for social apps, since usage happens in short trip-planning bursts, not daily habitual use. |

---

## 2. Traffic

**Base assumption:** each DAU generates a mix of search, browsing, and transactional requests per day.

| Request Type | Assumption | Calculation | Requests/day |
|---|---|---|---:|
| Searches | 5 searches/DAU (comparison shopping) | 2M × 5 | 10,000,000 |
| Booking requests | ~5% of DAU complete a booking | 2M × 5% | 100,000 |
| Payment requests | ~1.2× bookings (retries/splits) | 100K × 1.2 | 120,000 |
| Other (account, cart, history, browsing) | ~15 requests/DAU | 2M × 15 | ~30,000,000 |
| **Total** | | | **~40,000,000/day** |

**Average RPS**
```
40,000,000 ÷ 86,400 ≈ 463 RPS
```

**Peak RPS**
Peak factor of **4×** — global travel traffic clusters around business hours/evenings across timezones, weekends, and holiday/sale periods (less extreme than flash-sale e-commerce, which can hit 10×+).
```
463 × 4 ≈ 1,850 RPS
```

---

## 3. Read vs Write

| Type | Composition | Requests/day |
|---|---|---:|
| Reads | Searches (10M) + browsing/account/history (~25M) | 35,000,000 |
| Writes | Bookings (0.1M) + Payments (0.12M) + cart/profile updates (~5M) | ~5,220,000 |

**Read/Write ratio ≈ 85 : 15 (roughly 6–7 : 1)** — expected, since browsing/searching vastly outweighs actual transactions.

---

## 4. Bookings

```
Bookings/day   = 100,000
Bookings/month = 100,000 × 30  = 3,000,000
Bookings/year  = 100,000 × 365 ≈ 36,500,000
```

**Breakdown by category:**

| Category | Share | Bookings/day |
|---|---:|---:|
| Flights | 40% | 40,000 |
| Hotels | 35% | 35,000 |
| Car Rentals | 15% | 15,000 |
| Activities | 10% | 10,000 |

---

## 5. Storage (Transactional Data)

| Entity | Avg Record Size | Records/day | Reasoning | Storage/day | Storage/year |
|---|---:|---:|---|---:|---:|
| Users (new signups) | 2 KB | 50,000 | Assumed average user growth for a large-scale platform | 100 MB | ~36.5 GB |
| Flight Bookings | 1.5 KB | 40,000 | ~40% of all bookings; flight-specific booking data | 60 MB | ~21.9 GB |
| Hotel Bookings | 1.5 KB | 35,000 | ~35% of all bookings; hotel-specific booking data | 52.5 MB | ~19.2 GB |
| Car Bookings | 1.5 KB | 15,000 | ~15% of all bookings; car rental booking data | 22.5 MB | ~8.2 GB |
| Activity Bookings | 1.5 KB | 10,000 | ~10% of all bookings; activity-specific booking data | 15 MB | ~5.5 GB |
| Payments | 1 KB | 120,000 | Payment method, amount, gateway reference | 120 MB | ~43.8 GB |
| Transactions/Ledger | 0.5 KB | 180,000 | Ledger entries including refunds and adjustments | 90 MB | ~32.9 GB |
| **Total (raw)** | | | | **~460 MB/day** | **~168 GB/year** |

**Index & metadata overhead:** add **~40%** for indexes, foreign keys, timestamps, audit columns, and other database metadata.

```text
168 GB × 1.4 ≈ 235 GB/year (effective growth)
```

**Storage after 1 year:**
```
 235 GB (year 1 growth)

```

**Storage after 5 years:**
```
235 × 5
= 1,175 GB
≈ 1.18 TB
```

---

## 6. Bandwidth

| Metric | Assumption | Reasoning |
|---|---|---|
| Avg request size | 2 KB | Small JSON payloads (filters, form data, headers) |
| Avg response size | 20 KB (blended) | Search responses are large (~50 KB, many listings); other responses smaller (~5–10 KB) |

```
Incoming traffic/day = 40,000,000 × 2 KB  ≈ 80 GB/day
Outgoing traffic/day = 40,000,000 × 20 KB ≈ 800 GB/day

Monthly bandwidth:
Incoming/month = 80 GB × 30  ≈ 2.4 TB
Outgoing/month = 800 GB × 30 ≈ 24 TB
Total/month    ≈ 26.4 TB
```

---

## 7. Peak Traffic Scenarios

| Multiplier | Requests/day | Avg RPS | Peak RPS (4× factor) | Outgoing BW/day |
|---|---:|---:|---:|---:|
| 1× (baseline) | 40,000,000 | 463 | 1,850 | 800 GB |
| 2× | 80,000,000 | 926 | 3,700 | 1,600 GB |
| 5× | 200,000,000 | 2,315 | 9,260 | 4,000 GB |
| 10× | 400,000,000 | 4,630 | 18,520 | 8,000 GB |

---

## 📌 Final Summary

| Metric | Estimate |
|---|---:|
| Registered Users | 100 million |
| MAU | 20 million |
| DAU | 2 million |
| Searches/day | 10 million |
| Bookings/day | 100,000 |
| Requests/day | ~40 million |
| Average RPS | ~463 |
| Peak RPS | ~1,850 (4× factor) |
| Read/Write Ratio | ~85:15 (~6–7:1) |
| Storage/year | ~235 GB (growth, with overhead) |
| Storage/5 years | ~1.18 TB (cumulative, with overhead) |
| Bandwidth/month | ~26.4 TB |

---

*Note: This is a back-of-the-envelope estimate using rounded, realistic assumptions — not exact production figures. No architecture or infrastructure decisions are included.*
