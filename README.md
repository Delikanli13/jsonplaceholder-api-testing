# API Test Suite — JSONPlaceholder

![Newman API Tests](https://github.com/Delikanli13/jsonplaceholder-api-testing/actions/workflows/newman.yml/badge.svg)

Automated API test suite for the [JSONPlaceholder](https://jsonplaceholder.typicode.com) API, built with Postman and Newman. Runs automatically on every push via GitHub Actions.

## What this project covers

- Smoke testing across multiple endpoints
- Reading and filtering data with query parameters
- Full CRUD operations (GET, POST, PUT, PATCH, DELETE)
- Request chaining with dynamic collection variables
- Data-driven testing with CSV datasets
- JSON schema validation on responses
- Positive and negative test scenarios
- CI/CD pipeline via GitHub Actions

## Tech stack

| Tool | Purpose |
|---|---|
| Postman | API test authoring |
| Newman | CLI test runner |
| GitHub Actions | CI/CD pipeline |

## Collections

| Collection | Purpose |
|---|---|
| JSONPlaceholder-Smoke | Smoke tests across main endpoints |
| JSONPlaceholder-CRUD | Full CRUD, data-driven and schema validation tests |

## Test coverage

| Request | Method | Collection | Assertions |
|---|---|---|---|
| Get all posts | GET | Smoke | Status, response time, array structure |
| Get all users | GET | Smoke | Status, response time, array structure, email field |
| Get all todos | GET | Smoke | Status, response time, array structure |
| Single post by ID | GET | CRUD | Status, object structure, schema validation |
| Posts by userId | GET | CRUD | Status, array structure, userId filter, schema |
| Todos by userId | GET | CRUD | Status, array structure, completed boolean, schema |
| Negative test | GET | CRUD | 404 on invalid endpoint |
| Create post | POST | CRUD | Status 201, object structure, data matching |
| Update post | PUT | CRUD | Status, updated values |
| Patch post | PATCH | CRUD | Status, patched values |
| Delete post | DELETE | CRUD | Status, empty response |
| Negative PUT | PUT | CRUD | 500 on non-existent resource |
| Data-driven post | POST | CRUD | Status, data file matching across 4 iterations |

## How to run locally

**Prerequisites:** Node.js installed

**Install Newman:**
```bash
npm install -g newman
```

**Clone the repo:**
```bash
git clone https://github.com/Delikanli13/jsonplaceholder-api-testing.git
cd jsonplaceholder-api-testing
```

**Run smoke tests:**
```bash
newman run "JSONPlaceholder-Smoke.postman_collection.json" --environment "JSONPlaceholder.postman_environment.json"
```

**Run CRUD tests:**
```bash
newman run "JSONPlaceholder-CRUD.postman_collection.json" --environment "JSONPlaceholder.postman_environment.json" --iteration-data posts-data.csv
```

## CI/CD

Runs automatically on every push to `main` via GitHub Actions. View run history in the [Actions tab](https://github.com/Delikanli13/jsonplaceholder-api-testing/actions).

## Key learnings

- JSONPlaceholder returns `500` instead of `404` on PUT requests to non-existent resources — documented and asserted accordingly
- Data-driven testing with CSV allows broad input coverage from a single request
- Schema validation catches structural API changes that value assertions would miss