---
type: Article
tags:
  - monorepo
  - project-structure
  - software-architecture
  - engineering
created: 2025-10-26 - 02:24
updated: 2025-10-26 - 02:24
---
# The Ingredients of a Productive Monorepo

## Summary

Implementing a monorepo architecture is a major engineering effort that should be driven by a desire for organizational consistency and shared tooling, not by a misguided attempt to copy large tech companies. The core challenge is that standard developer tools are often O(repo) (scale with repository size), but a productive monorepo demands tools that are O(change) (scale with the size of the change). Thus, an organization must be prepared to invest in building or adapting specialized tools for core functions like source control, building, testing, and continuous integration/delivery to ensure performance and developer experience as the codebase grows.

## Key Points

- **The Golden Rule for Tooling:** 
	- The guiding principle for all monorepo-related development tools is that any operation that needs to be fast must be O(change) and not O(repo). This means that a process's speed must be determined by the specific changes submitted, preventing build times or status checks from slowing down as the general repository size increases.
- **Target Determination for Efficiency:** 
	- To address scaling in building and testing, a crucial component is a target determinator. This tool inspects the project's build graph and a code change to calculate the minimal, specific set of build artifacts and tests that have been directly or indirectly affected, ensuring developers run necessary validation steps.
- **Source Control Scaling:** 
	- Conventional source control systems like Git were not designed for large, centralized monorepos and experience performance degradation as history and file count grow. To compensate, scaled-up source control must support working on subsets of the repository using methods like sparse checkout or virtual filesystems, which download or present files relevant to the current task.
- **The Atomic Deployment Illusion:** 
	- The monorepos primary risk is the false sense of security that comes from making a single, atomic commit (e.g., updating a service interface and all its clients at once). Because services are deployed asynchronously, a single atomic commit in the repository will still break in production unless the continuous delivery system has controls to check service contracts before deployment.
- **CI Tradeoffs:** 
	- The Continuous Integration (CI) system must manage a merge queue, which forces a difficult balance between throughput (how fast changes are merged) and correctness (ensuring the main branch remains stable). Organizations must decide which cost they are willing to tolerate—a slower queue with higher correctness, or faster merging with a higher risk of introducing bugs.

## Personal Thoughts

...

## Examples

...

## References

- https://blog.swgillespie.me/posts/monorepo-ingredients/
