---
name: public-transport-victoria-plan-ticketing
description: Locate nearby ticket outlets and estimate a fare between zones.
api: ../openapi/public-transport-victoria-timetable-openapi.yml
operations:
- Outlets_GetOutletsByGeolocation
- Outlets_GetAllOutlets
- FareEstimate_GetFareEstimateByZone
---

# Find myki outlets and estimate a fare

## Steps
1. Call `Outlets_GetOutletsByGeolocation` with latitude,longitude (or `Outlets_GetAllOutlets`).
2. Call `FareEstimate_GetFareEstimateByZone` with minZone and maxZone.

## Rules
- Auth: append `devid` and `signature` query parameters to every request; see http://ptv.vic.gov.au/ptv-timetable-api/ for how to calculate the signature.
- All operations are GET and read-only, so retries are safe.
- `route_type` values come from `RouteTypes_GetRouteTypes`; do not hard-code them.
