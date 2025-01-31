There many ways to code a project, and the most used ones are Monolith and Microsservices.


## Monolith
Imagine a game that runs on the mobile and web enviroment. There we'll have many contexts to cover, as example a User, Inventory, Trading, etc, all of this contexts will be saved and processed on the same Server, and salved on the same database.
This structure is called Monolith, because every part of the project share the same codebase and structure. And all of these will be deployed at the same time.

### Pros
- Convenient for new projects
- Tools mostly focused on them
- Great code reuse
- Easier to run locally
- Easier to debug and troubleshoot
- One thing to build
- One thing to deploy
- One thing to test end to end
- One thing to scale
### Cons
- Easily gets too complex to understand
- Merging code can be challeging
- Slows down IDEs
- Long build times
- Slow and infrequent deployments
- Long testing and stabilization periods
- Rolling back is all or nothing
- No isolation between modules
- Can be hard to scale
- Hard to adopt new tech
- 


