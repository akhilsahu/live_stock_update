# live_stock_update

Design a service that ingests real-time stock market price updates and supports querying current and historical prices as well as user-defined price alerts.
Endpoints

1. POST /prices
Accepts a batch of price updates or a stream of updates for multiple symbols, each with timestamp and price.
2. GET /price/{symbol}
Returns the latest price and timestamp for the given symbol.
3. GET /prices/history
Query parameters: symbol, start_timestamp, end_timestamp; returns time-series of prices in that window.
4. POST /alerts
Request body: symbol, threshold_price, direction (above or below), callback_url; creates a price alert.
5. GET /alerts/{alert_id}/status
Returns the current state of the alert (pending, triggered, delivered).


**Key Constraints**

1. Data volume: ingest up to 100 K updates per second across all symbols.

2. Query latency: serve current-price queries in under 50 ms.

3. History retention: store and serve at least 30 days of price history.

4. Alert latency: detect threshold crossings and invoke callback_url within 200 ms.

5. Reliability: no loss of updates; ensure ordering per symbol.

6. Observability: metrics on ingestion lag, pipeline errors, query latencies, and alert delivery success.

