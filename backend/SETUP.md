# Backend Setup Guide

## Installation

1. **Install Python dependencies**
   ```bash
   pip install -r requirements.txt
   ```

2. **Verify installation**
   ```bash
   python -c "import fastapi; print('FastAPI installed')"
   ```

## Running the Backend

### Development Mode
```bash
python app.py
```

The API will be available at `http://localhost:8000`

### With Uvicorn Directly
```bash
uvicorn app:app --reload --host 0.0.0.0 --port 8000
```

## API Documentation

Once running, visit:
- **Interactive API docs**: http://localhost:8000/docs
- **Alternative API docs**: http://localhost:8000/redoc

## Database

SQLite database is automatically created on first run as `app_config.db`

### Reset Database
```bash
rm app_config.db
python app.py
```

## Testing the API

### Using curl

```bash
# Health check
curl http://localhost:8000/health

# Compile a prompt
curl -X POST http://localhost:8000/compile \
  -H "Content-Type: application/json" \
  -d '{
    "prompt": "Build an e-commerce platform with product catalog and shopping cart",
    "context": "Enterprise-grade solution"
  }'

# Get compilation history
curl http://localhost:8000/history

# Get specific compilation
curl http://localhost:8000/compilation/1
```

### Using Python

```python
import requests

# Compile
response = requests.post('http://localhost:8000/compile', json={
    'prompt': 'Build a social network app',
    'context': 'Community platform'
})
result = response.json()
compilation_id = result['compilation_id']

# Get result
response = requests.get(f'http://localhost:8000/compilation/{compilation_id}')
config = response.json()
```

## Environment Variables

No environment variables required for basic setup.

## Troubleshooting

### Port Already in Use
```bash
# Find process using port 8000
lsof -i :8000

# Kill process (Linux/Mac)
kill -9 <PID>

# On Windows
netstat -ano | findstr :8000
taskkill /PID <PID> /F
```

### Import Errors
Ensure you're in the backend directory and Python path is correct:
```bash
python -c "import sys; print(sys.path)"
```

### Database Lock
If you get database lock errors:
1. Ensure only one instance is running
2. Delete database and restart
3. Check file permissions

## Pipeline Configuration

Each stage is independently implemented and can be tested:

```python
from pipeline.intent_extraction import IntentExtractor

extractor = IntentExtractor()
result = extractor.extract("Your prompt here")
print(result)
```

## Performance Tuning

- Compilation typically takes 1-3 seconds
- Database queries are optimized with indexes
- Use pagination for history (default 50 items)

## Logs

Enable detailed logging by adding to `app.py`:

```python
import logging
logging.basicConfig(level=logging.DEBUG)
```
