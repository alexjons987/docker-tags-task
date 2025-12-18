# Lab: Docker Tags – `latest` vs. version tags
## Part 1 – Simple image with latest (warm-up)
### Assignment
* Create a simple Node.js application
* Build a Docker image locally
* Tag the image with `latest`
* Push the image to Docker Hub
* Run the image from Docker Hub
### Requirements
* Use `docker build`
* Use `docker tag`
* Use `docker push`
* Run the image with `docker run`
* View output from the container
## Part 2 – latest is not the “latest version” (important concept)
### Important to understand first
`latest` is not:
* a magic version
* automatically the latest code
* safe to use in production

`latest` is:
* just a named tag
* something that can be overwritten at any time
### Demonstration of the problem
#### Assignment
* Modify the application to clearly show a new version
* Build a new image
* Push again to the same latest tag
* Run latest without changing the command
#### Expected behavior
* Same command
* Different result
### Requirements
* Same repository
* Same tag (latest)
* No change in the docker run command
* Show that the behavior changes
### Real-world consequence
* CI/CD can deploy new code by mistake
* Production can be changed without version control
* Rollback becomes difficult or impossible
## Part 3 – Proper versioning with tags
### Scenario
You are now responsible for making the system:
* reproducible
* secure
* rollbackable
### Task
* Create two version tags:
  * 1.0.0
  * 2.0.0
* Push both versions to Docker Hub
* Run each version explicitly
### Requirements
* Use the same image repo
* Use different version tags

Run:
* `docker run <image>:1.0.0`
* `docker run <image>:2.0.0`

* Show that the versions are stable and predictable
## Part 4 – Combine `latest` and version tags (best practice)
### Important concept
The same image can have multiple tags.
* `myapp:1.2.0`
* `myapp:1.2`
* `myapp:latest`

All point to the same image ID.
### Task
* Build an image
* Tag it with:
  * exact version (`1.0.1`)
  * minor version (`1.0`)
  * `latest`
* Push all tags
### Requirements
* All tags should point to the same image

Verify with:
* `docker images`
* `docker inspect`
## Part 5 – Reflection & Analysis
### Answer in writing
1. Why is `latest` inappropriate in production?
2. When can `latest` still be okay?
3. Which tag should CI/CD use?
4. How do you rollback with version tags?