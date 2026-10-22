---
name: public-transport-victoria-trace-a-service-run
description: From a route, list its runs, then fetch the stopping pattern for one run.
api: ../openapi/public-transport-victoria-timetable-openapi.yml
operations:
- Routes_OneOrMoreRoutes
- Routes_RouteFromId
- Directions_ForRoute
- Runs_ForRoute
- Runs_ForRunAndRouteType
- Patterns_GetPatternByRun
- Stops_StopsForRoute
---

# Trace a service run and its stopping pattern

## Steps
1. Find the route with `Routes_OneOrMoreRoutes` (or `Routes_RouteFromId`).
2. Get its directions with `Directions_ForRoute` and stops with `Stops_StopsForRoute`.
3. List runs with `Runs_ForRoute`; inspect one with `Runs_ForRunAndRouteType`.
4. Call `Patterns_GetPatternByRun` with run_ref and route_type for the stopping pattern.

## Rules
- Auth: append `devid` and `signature` query parameters to every request; see http://ptv.vic.gov.au/ptv-timetable-api/ for how to calculate the signature.
- All operations are GET and read-only, so retries are safe.
- `route_type` values come from `RouteTypes_GetRouteTypes`; do not hard-code them.
