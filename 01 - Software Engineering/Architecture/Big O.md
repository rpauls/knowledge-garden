---
type: Article
tags:
  - software-architecture
  - engineering
  - high-level-perspective
created: 2025-10-25 - 21:12
updated: 2025-10-25 - 21:12
---
# Big O

## Summary

The article introduces Big O notation as a way to describe how a function’s runtime grows with input size, without relying on actual clock time. It emphasizes that Big O focuses on growth rates (constant, logarithmic, linear, quadratic, etc.) rather than exact durations, allowing developers to compare algorithm efficiency abstractly. Interactive visualizations illustrate each class, showing how adding elements to an input affects the total operations required. The piece also cautions that theoretical complexity isn’t a substitute for real‑world testing—actual performance can differ due to constants, hardware, and language overhead, so developers should benchmark code before and after changes.

## Key Points

- **Growth‑Based Metric** 
	- Big O measures how runtime scales as input size increases, ignoring absolute time values.
- **Common Classes** 
	- The article covers four typical categories: constant O(1), logarithmic O(log n), linear O(n), and quadratic O(n²), each illustrated with interactive examples.
- **Abstract Comparison** 
	- By focusing on growth rates, Big O lets developers compare algorithms without needing exact timing measurements.
- **Real‑World Testing Needed** 
	- Complexity analysis doesn’t replace empirical benchmarking; actual performance depends on factors like hardware, language, and hidden constants.

## Subtopics

...

## Personal Thoughts

...

## Examples

...

## References

- https://samwho.dev/big-o/
