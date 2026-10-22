---
name: public-transport-victoria-find-next-departures
description: Resolve a stop by name or location, then list upcoming departures (with real-time where available).
api: ../openapi/public-transport-victoria-timetable-openapi.yml
operations:
- Search_Search
- Stops_StopsByGeolocation
- RouteTypes_GetRouteTypes
- Departures_GetForStop
- Departures_GetForStopAndRoute
---

# Find next departures from a stop

## Steps
1. Call `RouteTypes_GetRouteTypes` to learn the route_type codes (train, tram, bus...).
2. Resolve the stop: `Search_Search` with the stop name, or `Stops_StopsByGeolocation` with latitude,longitude.
3. Call `Departures_GetForStop` with route_type and stop_id; narrow with `Departures_GetForStopAndRoute` when the user names a route.

## Rules
- Auth: append `devid` and `signature` query parameters to every request; see http://ptv.vic.gov.au/ptv-timetable-api/ for how to calculate the signature.
- All operations are GET and read-only, so retries are safe.
- `route_type` values come from `RouteTypes_GetRouteTypes`; do not hard-code them.
