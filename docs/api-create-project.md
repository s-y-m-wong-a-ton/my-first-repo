# Create Project

Creates a new project in TaskFlow.

the the

**Base URL:** `https://api.taskflow.com`

**Endpoint:** `POST /api/v1/projects`

## Authentication

Requires API key authentication. Include `Authorization: Bearer YOUR_API_KEY` header in all requests. See [Authentication](./authentication.md) for details.

## Request 

### Request Headers

The following table lists request headers you can use to make API calls to TaskFlow.

| Header | Required | Description |
|--------|----------|-------------|
| `Authorization` | Yes | Bearer token for authentication. Format: `Bearer YOUR_API_KEY` |
| `Content-Type` | Yes | The media type of the resource. Format: `application/json` |
| `Accept` | No | Response format. Default: `application/json` |

### Request Body

The following table lists the parameters (including requirements for each parameter) that you must include in the JSON you send to TaskFlow. 

| Parameter name | Type | Required | Description | Validation rules |
| -------------- | ---- | -------- | ----------- | ---------------- |
| `name` | string | Yes | Project name | Must be 1 - 100 characters. Can't be only whitespace. |
| `description` | string | No | Project description | Maximum 500 characters |
| `due_date` | string | No | Project due date | Must be in ISO 8601 format (YYYY-MM-DD). Must be today or a future date. Example: 2025-03-15 |
| `priority` | string | No | Project priority level | Must be one of: "low", "medium", "high". Default: "medium" |
| `team_members` | array of strings |  No | User identifiers to add to project | Each user identifier must reference an existing user |

### Example request

```
POST https://api.taskflow.com/api/v1/projects
Authorization: Bearer sk_live_12345
Content-Type: application/json
{
  "name": "Website Redesign",
  "description": "Complete overhaul of company website",
  "due_date": "2026-03-15",
  "priority": "high"
}
```

`sk_live_12345` is an API key in the example shown above.

## Response

### Success (201 Created)

Returns the project object if the project was successfully created.

**Response fields:**

| Field | Type | Description |
| ----- | ---- | ----------- |
| `id` | string | Unique project identifier. Use this ID in next API calls to reference this project. Format: `proj_` followed by alphanumeric characters. |
| `name` | string | Project name |
| `description` | string | Project description |
| `due_date` | string | Project due date in ISO 8601 format (YYYY-MM-DD) |
| `priority` | string | Project priority level. Possible values: `low`, `medium`, `high`. |
| `team_members` | array of strings | Unique identifiers of the users assigned to the project. Format of an identifier: `user_` followed by alphanumeric characters. |
| `created_at` | string | Timestamp when the project was created, in ISO 8601 format with UTC timezone. Example: 2025-12-28T10:30:00Z |
| `created_by` | string | Unique identifier of the project creator. Format: `user_` followed by alphanumeric characters. |
| `status` | string | Current project status. Always `active` for newly created projects. Possible values: `active`, `completed`, `archived` |

**Example Response:**

```json
{
  "id": "proj_abc123",
  "name": "Website Redesign",
  "description": "Complete overhaul of company website",
  "due_date": "2026-03-15",
  "priority": "high",
  "team_members": ["user_xyz789"],
  "created_at": "2025-12-28T10:30:00Z",
  "created_by": "user_xyz789",
  "status": "active"
}
```

### Errors

#### 400 Bad Request

**Problem:** After submitting a request, *400 Bad Request* is returned.

**Cause:** The request is malformed - either the JSON syntax is invalid or required headers are missing.

**Solution:** 
- Verify your JSON is valid (use a JSON validator)
- Ensure Content-Type header is set to `application/json`
- Check that the request body isn't empty

**Example:**
```json
{
  "error": "BAD_REQUEST",
  "message": "Invalid JSON syntax in request body",
  "status": 400
}
```

#### 401 Unauthorized

**Problem:** After submitting a request, *401 Unauthorized* is returned.

**Cause:** Authentication failed due to your API key being invalid or the `Authorization` header being improperly formatted.

**Solution:** Check that your API key is valid and properly formatted in the `Authorization` header.

**Example:**
```json
{
  "error": "UNAUTHORIZED",
  "message": "Invalid or missing API key.",
  "status": 401
}
```

#### 403 Forbidden

**Problem:** You are trying to create a project but error *403 Forbidden* is returned.

**Cause:** You don't have permission to create projects. 

**Solution:** Consult your administrator for access rights.

**Example:**
```json
{
  "error": "FORBIDDEN",
  "message": "You do not have permission to create this resource.",
  "status": 403
}
```

#### 422 Unprocessable Entity

**Problem:** You have submitted data to create a project but error *422 Unprocessable Entity* is returned.

**Cause:** Your JSON is formatted correctly, but the content fails business logic or validation rules, for example, leaving a required field such as the project's name empty or entering an invalid date format. 

**Solution:** Double-check the validation rules listed in the table under *Request Body* and ensure that all required fields are in the JSON you are sending to the server.

**Example:**
```json
{
  "error": "UNPROCESSABLE_ENTITY",
  "message": "Validation failed",
  "status": 422,
  "details": [
    {
      "field": "name",
      "issue": "required field missing"
    }
  ]
}
```
Or for invalid values:

```json
{
  "error": "UNPROCESSABLE_ENTITY",
  "message": "Validation failed",
  "status": 422,
  "details": [
    {
      "field": "priority",
      "value": "super-urgent",
      "issue": "must be one of: low, medium, high"
    }
  ]
}
```

## Code examples

### cURL

```bash
curl -X POST "https://api.taskflow.com/api/v1/projects" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Website Redesign",
    "description": "Complete overhaul of company website",
    "due_date": "2026-03-15",
    "priority": "high"
  }'
```
Or

```bash
curl -X POST "https://api.taskflow.com/api/v1/projects" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d @data.json
```

where `@data.json` is a file containing the JSON to submit. The content of this file is displayed below.


```json
{
  "name": "Website Redesign",
  "description": "Complete overhaul of company website",
  "due_date": "2026-03-15",
  "priority": "high"
}
```

### JavaScript

```javascript
async function createProject(projectData) {
  const url = 'https://api.taskflow.com/api/v1/projects';
  const token = process.env.TASKFLOW_API_KEY; // Use environment variables, never hardcode
  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Authorization': `Bearer ${token}`,
        'Accept': 'application/json'
      },
      // Convert the JavaScript object into a JSON string
      body: JSON.stringify(projectData)
    });

    if (!response.ok) {
      const errorDetail = await response.json();
      throw new Error(`Server Error: ${response.status} - ${errorDetail.message}`);
    }

    const data = await response.json();
    console.log('Success! Project Created:', data);
    return data;
  } catch (error) {
      console.error('Request Failed:', error.message);
  }
}

// Example usage:
const newProject = {
  name: "Website Redesign",
  description: "Complete overhaul of company website",
  due_date: "2026-03-15",
  priority: "high"
};

const result = await createProject(newProject);

if (result) {
    alert(`Success! Created project with ID: ${result.id}`);
    // Do something meaningful with the data that was returned 
} else {
    alert("Something went wrong. Check the console.");
}
```
 
 # This Is A Title Case Header
Click here to see more.