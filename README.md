# 🌍 Multi-Agent Travel Planning System

A comprehensive travel planning system built with Agent2Agent (A2A) protocol, featuring specialized AI agents for hotel booking, car rentals, currency conversion, and travel coordination.

## 🏗️ System Architecture

- **Travel Planner Agent** (Google ADK + A2A Protocol) - Master coordinator on port 10001
- **Hotel Booking Agent** (CrewAI + OpenAI) - Hotel search and booking on port 10002  
- **Car Rental Agent** (LangGraph + OpenAI) - Car rental options on port 10003
- **Currency Agent** (LangGraph + OpenAI) - Currency conversion and exchange rates on port 10004
- **Streamlit UI** - User-friendly web interface

## 🚀 Quick Start

### 1. Environment Setup

Copy the environment template and add your API keys:
```bash
cp .env.example .env
# Edit .env with your actual API keys
```

Required API keys:
- `OPENAI_API_KEY` - For OpenAI GPT-4o (all agents)
- `GOOGLE_API_KEY` - For Google ADK (Travel Planner Agent)
- `SERPER_API_KEY` - For real-time search (optional)

### 2. Install Dependencies

For each agent, create virtual environment and install dependencies using `uv`:

```bash
# Hotel Booking Agent
cd hotel_booking_agent_crewai
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt

# Car Rental Agent  
cd ../car_rental_agent_langgraph
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt

# Travel Planner Agent
cd ../travel_planner_agent_adk
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt

# Currency Agent
cd ../currency_agent_langhraph
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt

# Streamlit UI (global environment)
cd ..
uv venv
source .venv/bin/activate
uv pip install -r streamlit_requirements.txt
```

### 3. Start All Agents

Open 4 separate terminals and run each agent in its virtual environment:

**Terminal 1 - Hotel Booking Agent:**
```bash
cd hotel_booking_agent_crewai/app
source ../.venv/bin/activate
python simple_executor.py
```

**Terminal 2 - Car Rental Agent:**
```bash
cd car_rental_agent_langgraph/app
source ../.venv/bin/activate
python simple_executor.py
```

**Terminal 3 - Currency Agent:**
```bash
cd currency_agent_langhraph/app
source ../.venv/bin/activate
python simple_executor.py
```

**Terminal 4 - Travel Planner Agent:**
```bash
cd travel_planner_agent_adk/app
source ../.venv/bin/activate
python simple_executor.py
```

### 4. Launch the UI

**Terminal 5 - Streamlit App:**
```bash
streamlit run streamlit_travel_app.py
```

Open http://localhost:8501 in your browser.

## 🧪 Testing

Test individual agents:
```bash
# Test hotel agent
cd hotel_booking_agent_crewai && source .venv/bin/activate
python test_hotel_agent.py

# Test car rental agent
cd car_rental_agent_langgraph && source .venv/bin/activate
python test_car_rental_agent.py

# Test currency agent
cd currency_agent_langhraph && source .venv/bin/activate
python test_currency_agent.py

# Test travel planner
cd travel_planner_agent_adk && source .venv/bin/activate
python test_travel_planner.py

# Test entire system (from root directory)
python test_all_agents.py
```

## 📚 Usage

1. Enter your travel details (destination, dates, budget, guests)
2. The system coordinates with specialized agents:
   - Hotel agent searches for accommodations
   - Car rental agent finds vehicle options
   - Currency agent provides exchange rates and conversions
   - Travel planner creates comprehensive itinerary
3. Download your complete travel plan

## 🔗 API Endpoints

Each agent exposes standard endpoints:
- `/health` - Health check
- `/agent_card` - Agent metadata
- `/chat` - Main interaction endpoint

## 🛠️ Development

The system follows A2A protocol standards for agent communication, enabling:
- Distributed agent architecture
- Standardized inter-agent messaging
- Scalable agent discovery
- Framework-agnostic integration

## 📦 Project Structure

```
travel_planning_system/
├── hotel_booking_agent_crewai/     # CrewAI-based hotel agent
│   ├── app/                        # Main application code
│   │   ├── agent.py               # Agent implementation
│   │   ├── agent_executor.py      # A2A protocol executor
│   │   └── simple_executor.py     # REST API executor
│   ├── requirements.txt
│   └── test_hotel_agent.py
├── car_rental_agent_langgraph/     # LangGraph-based car agent
│   ├── app/                        # Main application code
│   │   ├── agent.py               # Agent implementation
│   │   ├── agent_executor.py      # A2A protocol executor
│   │   └── simple_executor.py     # REST API executor
│   ├── requirements.txt
│   └── test_car_rental_agent.py
├── currency_agent_langhraph/       # LangGraph-based currency agent
│   ├── app/                        # Main application code
│   │   ├── agent.py               # Agent implementation
│   │   ├── agent_executor.py      # A2A protocol executor
│   │   └── simple_executor.py     # REST API executor
│   ├── requirements.txt
│   └── test_currency_agent.py
├── travel_planner_agent_adk/       # Google ADK orchestrator
│   ├── app/                        # Main application code
│   │   ├── agent.py               # Agent implementation
│   │   ├── agent_executor.py      # A2A protocol executor
│   │   ├── simple_executor.py     # REST API executor
│   │   └── remote_agent_connection.py # A2A client wrapper
│   ├── requirements.txt
│   └── test_travel_planner.py
├── streamlit_travel_app.py         # Web interface
├── test_all_agents.py             # System tests
└── README.md                      # This file
```

## 🚧 Troubleshooting

- Ensure all agents are running before starting the UI
- Check that all required API keys are set in `.env`
- Verify ports 10001, 10002, 10003, 10004 are available
- Run individual agent tests to isolate issues
- Make sure each agent's virtual environment is activated
- Check agent logs for specific error messages