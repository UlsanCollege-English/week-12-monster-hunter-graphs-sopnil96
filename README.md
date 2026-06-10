[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/80z-ZS6n)
# Week 12: Monster Hunter Graphs

## Student
Name: Istiak Sopnil
Student ID: sopnil96

## Summary
This assignment builds undirected and weighted graphs to represent monster sighting locations and the routes connecting them. Locations are nodes in the graph and routes are edges between them. The weighted graph stores danger scores for each route, keeping the lowest score if duplicates appear. The most connected location is found by counting neighbors, and urgent sightings are prioritized using a min-heap. The hardest function was `build_weighted_hunter_map` due to handling duplicate routes and validating danger scores.

## Approach
- `build_hunter_map`: Looped over each edge and added both directions to the adjacency list, skipping duplicates by checking if the neighbor already exists.
- `build_weighted_hunter_map`: Same as above but stored danger scores in a nested dictionary. Raised `ValueError` for non-positive scores and kept the lowest score for duplicate routes.
- `map_summary`: Counted keys for locations and summed all neighbor list lengths divided by 2 for undirected routes.
- `most_connected_location`: Used `min()` with a key that sorts by negative neighbor count first, then alphabetically to break ties.
- `priority_hunt_order`: Used `heapq.heapify` on the reports list and popped locations one by one from lowest to highest priority number.

## Complexity

### `build_hunter_map`
- Time: O(E)
- Space: O(V + E)
- Why: Loops over each edge once; stores all vertices and edges in the adjacency list.

### `build_weighted_hunter_map`
- Time: O(E)
- Space: O(V + E)
- Why: Loops over each edge once; stores all vertices and weighted edges in nested dictionaries.

### `map_summary`
- Time: O(V + E)
- Space: O(1)
- Why: Sums the length of all neighbor lists which covers all edges; no extra storage needed.

### `most_connected_location`
- Time: O(V)
- Space: O(1)
- Why: Scans all locations once to find the maximum degree.

### `priority_hunt_order`
- Time: O(n log n)
- Space: O(n)
- Why: `heapq.heapify` is O(n) and each `heappop` is O(log n) for n items.

## Edge-Case Checklist
- [x] Empty graph
- [x] One route
- [x] Duplicate routes
- [x] Disconnected locations
- [x] Tie for most connected location
- [x] Positive weighted routes
- [x] Invalid zero or negative danger score
- [x] Empty priority report list

## Tests
Paste the result of your test run.
```bash
pytest -q
```
Result:
```text

```

## Assistance & Sources
AI used? Yes
If yes, what did it help with?
- Implementation guidance, complexity analysis, and edge case handling.

Other sources used:
- Python Official Documentation for `heapq`