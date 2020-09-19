# Demo Spring Versioning

### API Versioning Strategies

- URI - simplicity (versioning in URI): /v1, /v2
- Custom Header - single URI (keep versioning out of the URI): Accept-version: v1, Accept-version: v2

### Deployment

- Using branching and load balancer
- Versions of the application deployed behind a load balancer or proxy server which will look for 
  - v1 or v2 in the URI path and route the traffic to the appropriate deployment
  - custom HTTP header you defined and route calls based on the defined values you have set
    - should define a default rule to remind clients that they need to include the custom header called Accept-version in Headers in case they missing and show supported versions

## Versioning

- Version 1: **v1** branch
- Version 2: **master** branch

## Examples

```bash
git checkout v1
# health check
curl --location --request GET 'http://localhost:8080/actuator/health'
# get all employees
curl --location --request GET 'http://localhost:8080/v1/employees'
# create a new employee
curl --location --request POST 'http://localhost:8080/v1/employees' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "spring",
    "title": "developer"
}'
# get schedule
curl --location --request GET 'http://localhost:8080/v1/schedule'
```
