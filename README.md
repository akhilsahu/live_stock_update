# live_stock_update

Design a service that ingests real-time stock market price updates and supports querying current and historical prices as well as user-defined price alerts.
Endpoints

POST /prices
Accepts a batch of price updates or a stream of updates for multiple symbols, each with timestamp and price.
GET /price/{symbol}
Returns the latest price and timestamp for the given symbol.
GET /prices/history
Query parameters: symbol, start_timestamp, end_timestamp; returns time-series of prices in that window.
POST /alerts
Request body: symbol, threshold_price, direction (above or below), callback_url; creates a price alert.
GET /alerts/{alert_id}/status
Returns the current state of the alert (pending, triggered, delivered).
Key Constraints

Data volume: ingest up to 100 K updates per second across all symbols.
Query latency: serve current-price queries in under 50 ms.
History retention: store and serve at least 30 days of price history.
Alert latency: detect threshold crossings and invoke callback_url within 200 ms.
Reliability: no loss of updates; ensure ordering per symbol.
Observability: metrics on ingestion lag, pipeline errors, query latencies, and alert delivery success.
Paramphraset the scnario and identify goals
