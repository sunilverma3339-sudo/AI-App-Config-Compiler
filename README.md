# AI App Config Compiler

A full-stack application that converts open-ended product prompts into strict valid JSON app configurations using a 7-stage pipeline.

## 🎯 Features

### Frontend (React + Vite + Tailwind CSS)
- **Prompt Input Area** - Natural language product descriptions
- **Stage-wise Pipeline Viewer** - Real-time visualization of all 7 pipeline stages
- **Final JSON Viewer** - Browse generated configuration in multiple views
- **Validation Report** - Detailed validation results with errors and warnings
- **Evaluation Metrics Dashboard** - Quality scores across 7 dimensions
- **Compilation History** - Track recent compilations
- **Professional Dark Theme** - Developer-tool style UI

### Backend (Python FastAPI)
- **7-Stage Pipeline Architecture**
  1. **Intent Extraction** - Parse user intent from prompts
  2. **System Design Layer** - Design system roles, entities, workflows
  3. **Schema Generation** - Generate UI, API, and database schemas
  4. **Validation Layer** - Validate configuration completeness and consistency
  5. **Repair Engine** - Fix validation errors automatically
  6. **Execution Simulator** - Simulate application execution flow
  7. **Evaluation Framework** - Quality assessment across multiple dimensions

- **SQLite Database** - Persistent storage of compilations and pipeline runs
- **Pydantic Models** - Strict type validation and JSON schema generation
- **RESTful API** - Complete compilation lifecycle management

### Output Configuration
The system generates comprehensive JSON configurations including:
- `app_name` - Generated application name
- `assumptions` - System assumptions and constraints
- `entities` - Data model with attributes and relationships
- `roles` - User roles and responsibilities
- `permissions` - Role-based access control
- `ui_schema` - Frontend pages and components
- `api_schema` - REST API endpoints and authentication
- `database_schema` - Database tables, relationships, and indexes
- `auth_rules` - Authentication and authorization rules
- `business_logic` - Business rules and triggers
- `validation_report` - Validation results
- `execution_simulation` - Execution flow simulation
- `evaluation_framework` - Quality metrics

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Node.js 16+
- npm

### Backend Setup

```bash
cd backend
pip install -r requirements.txt
python app.py
```

Backend runs on `http://localhost:8000`

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Frontend runs on `http://localhost:5173`

## 📋 API Documentation

### Compile Prompt
```
POST /compile
Content-Type: application/json

{
  "prompt": "Build an e-commerce platform where customers can browse products...",
  "context": "Optional additional context"
}

Response:
{
  "success": true,
  "compilation_id": 1,
  "config": { ... },
  "pipeline_stages": [ ... ]
}
```

### Get Compilation
```
GET /compilation/{compilation_id}
```

### Get History
```
GET /history?limit=50
```

### Health Check
```
GET /health
```

## 🧪 Test Prompts

The system includes 20 test prompts:
- **10 Normal Prompts**: E-commerce, Project Management, Social Networks, CRM, LMS, Health Tracking, Content Management, Booking Systems, Inventory, Video Streaming
- **10 Edge Cases**: Real-time Collaboration, Vague Requirements, Complex ML, Oversimplified, Hyperscale, Regulatory Compliance, Offline-First, IoT, Blockchain, Contradictory Requirements

## 📊 Pipeline Execution Flow

1. **Intent Extraction** (🎯)
   - Analyzes prompt to determine app type, target users, key features
   - Extracts primary purpose and complexity level

2. **System Design** (🏗️)
   - Creates user roles with permissions
   - Defines system entities and relationships
   - Designs workflows and generates assumptions

3. **Schema Generation** (📋)
   - Generates UI schema with pages and components
   - Creates API schema with endpoints and authentication
   - Generates database schema with tables and relationships

4. **Validation Layer** (✓)
   - Validates schema completeness
   - Checks configuration consistency
   - Verifies business logic requirements

5. **Repair Engine** (🔧)
   - Auto-repairs failed validations
   - Generates defaults for missing components
   - Only repairs failed sections, not entire config

6. **Execution Simulator** (⚡)
   - Simulates authentication flows
   - Simulates API calls
   - Simulates database operations
   - Identifies potential issues

7. **Evaluation Framework** (📊)
   - Scores completeness (0-100)
   - Scores consistency (0-100)
   - Scores security (0-100)
   - Scores scalability (0-100)
   - Scores maintainability (0-100)
   - Generates recommendations

## 🔧 Configuration

### Backend Configuration
- Database: SQLite (`backend/app_config.db`)
- API Host: `0.0.0.0:8000`
- CORS: Enabled for all origins

### Frontend Configuration
- Proxy: API calls to `http://localhost:8000`
- Theme: Dark mode with developer colors
- Build: Vite optimized production build

## 📁 Project Structure

```
.
├── backend/
│   ├── app.py                          # FastAPI application
│   ├── models.py                       # Pydantic models
│   ├── database.py                     # SQLite database
│   ├── test_prompts.py                 # Test data (20 prompts)
│   ├── requirements.txt                # Python dependencies
│   └── pipeline/
│       ├── intent_extraction.py        # Stage 1
│       ├── system_design.py            # Stage 2
│       ├── schema_generation.py        # Stage 3
│       ├── validation_layer.py         # Stage 4
│       ├── repair_engine.py            # Stage 5
│       ├── execution_simulator.py      # Stage 6
│       └── evaluation_framework.py     # Stage 7
├── frontend/
│   ├── index.html                      # Entry HTML
│   ├── package.json                    # npm dependencies
│   ├── vite.config.js                  # Vite configuration
│   ├── tailwind.config.js              # Tailwind CSS config
│   ├── postcss.config.js               # PostCSS config
│   └── src/
│       ├── App.jsx                     # Main component
│       ├── main.jsx                    # Entry point
│       ├── index.css                   # Tailwind CSS
│       ├── api.js                      # API client
│       └── components/
│           ├── PromptInput.jsx         # Prompt input
│           ├── PipelineViewer.jsx      # Pipeline visualization
│           ├── ConfigViewer.jsx        # Config browser
│           ├── ValidationReport.jsx    # Validation display
│           ├── EvaluationDashboard.jsx # Metrics dashboard
│           └── History.jsx             # History viewer
└── README.md
```

## 🎨 UI Features

- **Professional Dark Theme** - Clean, developer-friendly design
- **Responsive Layout** - Works on all screen sizes
- **Real-time Updates** - Pipeline stages show as they execute
- **Interactive Exploration** - Expandable sections, multiple views
- **Metric Visualizations** - Score gauges, progress bars, recommendations
- **Error Handling** - Clear error messages and recovery suggestions

## 🛠️ Technology Stack

### Frontend
- React 18
- Vite 5
- Tailwind CSS 3
- Axios

### Backend
- FastAPI
- Uvicorn
- Pydantic
- SQLite3
- Python 3.8+

## 📈 Metrics & Evaluation

The Evaluation Framework scores configurations on:
1. **Completeness** - Presence of all required components
2. **Consistency** - Alignment between roles, entities, and APIs
3. **Security** - Authentication, authorization, and permissions
4. **Scalability** - Design for horizontal scaling and performance
5. **Maintainability** - Documentation, naming conventions, separation of concerns
6. **Validation Success** - Passes validation checks
7. **Execution Readiness** - Simulation success rate

## 🔐 Security Features

- JWT token support in API schemas
- Role-based access control
- Permission definitions
- Rate limiting configuration
- CORS enabled
- Input validation with Pydantic

## 📝 Example Usage

```bash
# Start backend
cd backend
python app.py

# In another terminal, start frontend
cd frontend
npm run dev

# Open browser to http://localhost:5173

# Enter a prompt like:
# "Build an e-commerce platform with product catalog, shopping cart, and payment processing"

# Click "Generate Configuration"

# Explore the generated configuration through different tabs
```

## 🐛 Troubleshooting

### Backend won't start
- Ensure Python 3.8+ is installed
- Check all dependencies: `pip install -r requirements.txt`
- Verify port 8000 is available

### Frontend won't connect to API
- Ensure backend is running on http://localhost:8000
- Check browser console for CORS errors
- Verify vite proxy configuration

### Database errors
- SQLite database is auto-created on first run
- Check file permissions in backend directory
- Delete `app_config.db` to reset database

## 📄 License

MIT License - See LICENSE file for details

## 🤝 Contributing

Contributions welcome! Please follow these guidelines:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📧 Support

For issues and questions, please create an issue on the GitHub repository.
