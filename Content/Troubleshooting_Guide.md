# Troubleshooting Guide

## 401 Unauthorized
- **Issue**: Invalid or expired token.
- **Resolution**: Refresh the personal access token and update the `Authorization` header.

## 422 Unprocessable Entity
- **Issue**: Trying to access a non-public resource without access or sending request with empty query.
- **Resolution**:
  - Make sure you have access to the private resource or opt for public resources instead.
  - Ensure that the search query parameter (`q`) is not empty (for `/search/repositories` endpoint).

## 403 Forbidden (Rate Limit)
- **Issue**: API limit exceeded.
- **Resolution**:
  - `Retry-After` and `X-RateLimit-Reset` headers are used in `handle-rate-limits` function to determine retry time.
  - Make sure you are authorized: GitHub allows 5000 requests per hour for authorized users.

## 404 Not Found
- **Issue**: Requested resource does not exist (e.g., no `README` or `LICENSE`).
- **Resolution**: Conditional logic is used to handle absent files gracefully.
