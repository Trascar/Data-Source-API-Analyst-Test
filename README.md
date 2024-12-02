# Data-Source-API-Analyst-Test

## Overview
This repository contains the solution to the **Data Source API Analyst** challenge. The objective is to demonstrate proficiency in working with APIs, data extraction, error handling, and documentation. The implementation leverages the GitHub API to retrieve and process repository, commit, and content data based on specific client requirements.

---

## Repository structure
```
├── Content/
│ ├── API_Documentation.md # Detailed API usage and endpoints
│ ├── Data-Cleaning.md # Explanation of the data-cleaning process
│ ├── Troubleshooting_Guide.md # Guide for handling possible errors
├── Postman_Collection/
│ ├── API_Test.ipynb # Jupyter Notebook containing data extraction logic
│ ├── GitHub_API_Test.json # Exported Postman collection
├── README.md # Project overview and approach
```

---

## Client Requirements

### **Repository Search and Filtering**
- **Requirement**: Use the GitHub API to identify public repositories meeting the following criteria:
  - **Programming Language**: Python or JavaScript.
  - **Star Count**: At least 100 stars.
  - **Topics**: Tagged with "machine-learning" or "data-analysis."
- **Purpose**: Generate a curated list of repositories relevant for AI/ML research.

### **Commit History Retrieval**

- **Requirement**: Extract commit history for each selected repository, including:
  - **Commit Message**: Text of each commit message.
  - **Author Details**: Author name and email.
  - **Timestamp**: Exact date and time of the commit.
- **Purpose**: Analyze contributor activity and project progress over time.

### **File Content Retrieval**

- **Requirement**: Download the following specific files from each repository:
  - **README.md**: For insights into project purpose and documentation quality.
  - **LICENSE**: For understanding the terms of use.
- **Purpose**: Review and validate repository content for compliance and quality.

---

## Approach

### 1. API Research and Authentication
- **API Endpoints**:
  - `/search/repositories`: Retrieve repositories matching the filters.
  - `/repos/{owner}/{repo}/commits`: Extract commit history.
  - `/repos/{owner}/{repo}/readme`: Download `README.md` content.
  - `/repos/{owner}/{repo}/license`: Fetch licensing information.
- **Authentication**:
  - Used a personal access token via the `Authorization` header for authenticated requests.

### 2. Data Extraction
- **Pagination**:
  - Handled datasets exceeding 30 results using the `page` query parameter.
- **Rate Limits**:
  - Managed using `X-RateLimit-Reset` and `Retry-After` headers.
  - Implemented automatic retries for rate limit breaches.

### 3. Error Handling
- Implemented error management:
  - **401 Unauthorized**: Refreshed expired tokens.
  - **403 Forbidden (Rate Limit)**: Paused execution until limits reset.
  - **404 Not Found**: Skipped missing resources (e.g., absent `README.md` files).

 ---

## Reflection
This test successfully extracted data from 36 relevant repositories, including commit histories and specific files, meeting the client's requirements. The retrieved information can be used for further processing and analysis.
