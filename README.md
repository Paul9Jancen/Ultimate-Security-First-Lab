Serverless To-Do REST API (AWS)

A fully serverless To-Do REST API built on AWS using API Gateway, Lambda, and DynamoDB.
Designed for secure, scalable CRUD operations with browser access enabled and built entirely through the AWS Console.

Architecture
API Gateway (HTTP API)
        |
        v
AWS Lambda (TodoHandler)
        |
        v
DynamoDB Table (Todos)

Features

Full CRUD operations:

Create, Read (single and list), Update, Delete

Serverless architecture (no servers to manage)

Secure IAM permissions (least privilege)

CORS enabled for browser-based frontends

Free Tier safe

Implemented entirely in AWS Console (no CLI or Terraform)

Technologies Used
Service	Purpose
API Gateway (HTTP API)	Exposes REST endpoints
AWS Lambda (Python 3.11)	Serverless backend logic
DynamoDB	NoSQL database storage
IAM	Secure permissions
CloudWatch	Monitoring & logs
DynamoDB Table

Table Name: Todos
Partition Key: id (String)
Billing Mode: On-demand (PAY_PER_REQUEST)

API Endpoints
Method	Endpoint	Purpose
GET	/todos	List all todos
POST	/todos	Create a new todo
GET	/todos/{id}	Get a single todo
PUT	/todos/{id}	Update a todo
DELETE	/todos/{id}	Delete a todo

Base URL:
https://r9309x2rdl.execute-api.us-east-1.amazonaws.com

Lambda Environment Variables
Key	Value
TABLE_NAME	Todos
IAM Permissions

The Lambda role is restricted to only required DynamoDB actions:

dynamodb:GetItem

dynamodb:PutItem

dynamodb:UpdateItem

dynamodb:DeleteItem

dynamodb:Scan

How to Test (curl)
Create Todo
curl -X POST https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos \
  -H "Content-Type: application/json" \
  -d '{"task": "Finish AWS project"}'

List Todos
curl https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos

Get Todo
curl https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos/<id>

Update Todo
curl -X PUT https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos/<id> \
  -H "Content-Type: application/json" \
  -d '{"task": "Updated task"}'

Delete Todo
curl -X DELETE https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos/<id>

Browser Testing (JavaScript)
<script>
async function createTodo() {
    const response = await fetch('https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos', {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify({task: 'My first todo'})
    });
    const data = await response.json();
    console.log(data);
}

async function listTodos() {
    const response = await fetch('https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos');
    const data = await response.json();
    console.log(data);
}

createTodo();
listTodos();
</script>

Cost Control and Safety

DynamoDB uses On-demand billing (no capacity planning)

Lambda is only charged when invoked

API Gateway is charged per request

If unused, cost is near zero

Can be deleted anytime to prevent any cost
Final Notes

This project demonstrates a complete serverless backend built entirely in the AWS Console, with full CRUD, security, and browser compatibility. It is Free Tier safe and ready for frontend integration.
