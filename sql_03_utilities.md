# Utilities

## Turn Safe Mode Off

- In some cases we would want to turn it off. This way, sql will only provide warnings, but it won't stop actions from happening.
- It is as easy as this: `SET SQL_SAFE_UPDATES = 0`

## Create Random Numbers

- With **RAND**:
```
BEGIN;
UPDATE guides
SET guides_qty = RAND()*1000;
```
