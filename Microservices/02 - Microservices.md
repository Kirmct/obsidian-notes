## What are microservices
An architetural style that structures an application as a collection of independenlty depoyable services that are modeled around a business domain and are usually owned by a small team.
![[Pasted image 20250130090232.png]]

## Pros
- Small, easier to understand code base
- Quicker to build
- Independent, faster deployments and rollbacks
- Independently scalable
- Much better isolation from failures
- Designed for continous delivery
- Easier to adopt new, varied tech
- Grants autonomyu to teams and lets them work in parallel
## Cons
- Not easy to find the right set of services
- Adds the complexity of distributed systems
- Shared code moves to separate libraries
- No good tooling for distributed apps
- Releasing features across service is hard
- Hard to troubleshoot issues across services
- Can't use transactions across services
- Raises the required skillset for the team

## When to use microservices
- It's perfectly fine to start with a monolith, then move to microservices
- Start looking at microservices when
	- The code base size is more than what a small team can maintain
	- Teams can't move fast anymore
	- Builds become too slow due to large code base
	- Time to market is compromisse due to infrequent deployments and long verification times
- It's all about team autonomy!