# API Documentation

## Endpoints Used

- **`/search/repositories`**: Find repositories based on filters.
- **`/repos/{owner}/{repo}/commits`**: Retrieve commit history.
- **`/repos/{owner}/{repo}/readme`**: Fetch `README.md` content.
- **`/repos/{owner}/{repo}/license`**: Fetch licensing information.

## Request Parameters

- **`q`**: Search query (e.g., `language:Python stars:>100`).
- **`page`**: For pagination.

## Rate Limits

- **5,000 requests per hour** for authenticated users.
- Functions `is_rate_limit_exceeded()` and `handle_rate_limit()` manage retries after exceeding limits.

## Error Handling

- **404 errors**: For missing content.
- **403 errors**: For rate limits.
