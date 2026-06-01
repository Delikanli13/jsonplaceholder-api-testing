# API Test Suite — JSONPlaceholder

![Newman API Tests](https://github.com/Delikanli13/jsonplaceholder-api-testing/actions/workflows/newman.yml/badge.svg)

Automated API test suite for the [JSONPlaceholder](https://jsonplaceholder.typicode.com) API, built with Postman and Newman. Runs automatically on every push via GitHub Actions.

## What this project covers

- Smoke testing across multiple endpoints
- Response time assertions
- Array structure validation
- Field-level assertions

## Tech stack

| Tool | Purpose |
|---|---|
| Postman | API test authoring |
| Newman | CLI test runner |
| GitHub Actions | CI/CD pipeline |

## How to run locally

**Install Newman:**
```bash
npm install -g newman
```

**Clone the repo:**
```bash
git clone https://github.com/Delikanli13/jsonplaceholder-api-testing.git
cd jsonplaceholder-api-testing
```

**Run the collection:**
```bash
newman run "JSONPlaceholder-Practice.postman_collection.json" --environment "JSONPlaceholder.postman_environment.json"
```

## CI/CD

Runs automatically on every push to `main` via GitHub Actions. View run history in the [Actions tab](https://github.com/Delikanli13/jsonplaceholder-api-testing/actions).