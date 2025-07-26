# IT Support Request Classifier

An AI-powered IT support request classification system that automatically categorizes and routes IT support tickets.

## Features

- **Automatic Classification**: Uses Mistral-7B model to classify IT support requests
- **Structured Output**: Returns JSON with request type, urgency, routing info, and response message
- **REST API**: Flask-based API for easy integration
- **Input Validation**: Handles edge cases and validates user input
- **Health Check**: Monitoring endpoint for deployment

## API Endpoints

### POST /classify
Classifies an IT support request.

**Request Body:**
```json
{
  "query": "My laptop screen is broken and I have a meeting in an hour"
}
```

**Response:**
```json
{
  "request_type": "Hardware Issue",
  "description": "Laptop screen malfunction with urgent timeline",
  "urgency": "High",
  "auto_approval": "No",
  "response_message": "We understand the urgency of your laptop issue...",
  "route_to": "IT Desk"
}
```

### GET /health
Health check endpoint for monitoring.

## Deployment

### Environment Variables
Set the following environment variable:
- `HF_TOKEN`: Your Hugging Face API token

### For Heroku/Railway/Render:
1. Push to GitHub
2. Connect your repository
3. Set `HF_TOKEN` environment variable
4. Deploy

### Local Development
```bash
export HF_TOKEN="your_hugging_face_token"
pip install -r requirements.txt
python it_sup_mod.py
```

## Usage Example

```bash
curl -X POST http://your-app-url/classify \
  -H "Content-Type: application/json" \
  -d '{"query": "I forgot my password and cannot login"}'
```

## Input Validation
- Query must be 5-1000 characters
- Handles special characters safely
- Returns appropriate error messages
