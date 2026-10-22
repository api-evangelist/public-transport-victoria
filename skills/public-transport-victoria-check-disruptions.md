---
name: public-transport-victoria-check-disruptions
description: List current disruptions for the network, a route, a stop, or a route at a stop, and read one in detail.
api: ../openapi/public-transport-victoria-timetable-openapi.yml
operations:
- Disruptions_GetAllDisruptions
- Disruptions_GetDisruptionsByRoute
- Disruptions_GetDisruptionsByStop
- Disruptions_GetDisruptionsByRouteAndStop
- Disruptions_GetDisruptionById
- Disruptions_GetDisruptionModes
---

# Check service disruptions

## Steps
1. Optionally call `Disruptions_GetDisruptionModes` to interpret disruption modes.
2. Pick scope: `Disruptions_GetAllDisruptions`, `Disruptions_GetDisruptionsByRoute`, `Disruptions_GetDisruptionsByStop` or `Disruptions_GetDisruptionsByRouteAndStop`.
3. Fetch full detail with `Disruptions_GetDisruptionById`.

## Rules
- Auth: append `devid` and `signature` query parameters to every request; see http://ptv.vic.gov.au/ptv-timetable-api/ for how to calculate the signature.
- All operations are GET and read-only, so retries are safe.
- `route_type` values come from `RouteTypes_GetRouteTypes`; do not hard-code them.
