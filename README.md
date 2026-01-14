# 🏏 AI Cricket Analytics Project

A comprehensive cricket analytics platform that leverages machine learning, optimization, and LLMs to predict IPL player prices, build optimal squads, and provide cricket-focused insights through an intelligent chatbot.

---

## 📌 Overview

The **AI Cricket Analytics Project** is a Streamlit-based web application that unifies three core modules into a single analytics toolkit:

1. **Cricket Chatbot** – An LLM-powered assistant restricted to cricket-related queries.
2. **Player Price Predictor** – A Ridge Regression model that predicts player prices using IPL and T20 career statistics.
3. **Team Builder** – An optimization engine using PuLP to construct the best possible team from a given player pool based on a custom impact score.

This project is tailored for fantasy players, analysts, and cricket enthusiasts who want data-driven decision support for IPL and T20 contexts.

---

## 🔧 Features

### 1. Cricket Chatbot

- AI chatbot powered by the **Gemini API**.
- Carefully engineered prompts ensure the chatbot answers **only cricket-related** questions.
- Supports queries on rules, player performance, formats, strategies, and historical context.

### 2. Player Price Predictor

- Predicts player price based on **IPL and T20 career statistics**.
- Uses **Ridge Regression**, trained on **2024 and 2025 player data**.
- Incorporates high-level **feature engineering** to better model player performance and value.
- Input features include batting and bowling statistics (e.g., runs, average, strike rate, wickets, economy).

### 3. Team Builder (Squad Optimizer)

- Builds an **optimized team** from a user-defined player pool.
- Allows you to specify configuration requirements such as:
  - Number of batters, bowlers, all-rounders, and wicketkeepers.
  - Custom constraints for the type of team you want to build.
- Uses **PuLP** (linear programming) to select the best combination of players.
- Maximizes a **custom impact score** while strictly adhering to all constraints.

---

## 🧠 Methodology

### Price Prediction

- **Model**: Ridge Regression  
- **Training Data**: IPL/T20 player data from the **2024 and 2025 seasons**.  
- **Approach**:
  - Perform high-level feature engineering on batting and bowling statistics.
  - Capture form, consistency, and overall player value.
  - Train and validate the model to estimate player prices based on historical performance.

### Team Optimization

The team builder formulates team selection as an optimization problem:

- **Library**: PuLP (Python Linear Programming)  
- **Objective**: Maximize the **total team impact score**.  
- **Constraints** (examples):
  - Exact or minimum/maximum number of players per role (e.g., 4 batters, 3 bowlers).
  - Squad size.
  - Other structural constraints defined by the user.

---

## 📊 Impact Score Formulation

A unified **impact score** is used to compare and rank players across roles and formats. Separate formulas are defined for batting, bowling, and all-rounders.

### Batting Impact

#### Test Cricket

$$
\text{Batting Impact} = (\text{Average} \times 0.75) + \left(\frac{\text{Runs}}{\text{Innings}} \times 0.15\right) + \left(\frac{\text{Strike Rate}}{2} \times 0.10\right)
$$

#### ODI Cricket

$$
\text{Batting Impact} = \sqrt{\text{Batting Average} \times \text{Batting Strike Rate}} + (0.5 \times \text{BP})
$$

> **Note**: BP represents a Boundary Percentage

#### T20 Cricket

$$
\text{Batting Impact} = (\text{Strike Rate} \times 0.7) + (\text{Average} \times 0.3) + 0.7 \times (\text{Average} + \text{Strike Rate})
$$

---

### Bowling Impact

#### Test Cricket

$$
\text{Bowling Impact} = \frac{1000}{\text{Bowling Average}} + \left(\frac{100}{\text{Bowling Strike Rate}} \times 2\right)
$$

#### ODI & T20 Cricket

$$
\text{Bowling Impact} = \left(\frac{\text{Dot Percentage} \times \text{Wickets}}{\text{Economy}^2}\right) \times 100
$$

---

### All-Rounder Impact

$$
\text{All-rounder Impact} = \frac{\text{Batting Impact} + \text{Bowling Impact}}{2}
$$

---

These formulas allow the system to rank players quantitatively and enable the optimization engine to build the best possible team according to user requirements.

---


## 🛠 Tech Stack

| Component | Technology |
|---------|------------|
| Frontend | Streamlit |
| Backend | Python |
| Machine Learning | Scikit-learn |
| Optimization | PuLP |
| LLM | Google Gemini API |
| Data Processing | Pandas, NumPy |
| Model Serialization | Pickle (`.pkl`) |
---


## 📂 Project Structure

```text
AI-Cricket-Analytics-Project/
│
├── app.py                     # Full Code
├── requirements.txt           # Python dependencies
├── feature_columns.pkl        # Feature Model
├── ipl_price_model.pkl        # Price Model
├── ODI_output.json            # Sample ODI player data
├── test_output.json           # Sample Test player data
└── README.md                  # Project documentation
```
## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- `pip or uv` for dependency management
- Gemini API key (for the chatbot module)

### Setup

```bash
# Clone the repository
git clone https://github.com/Mayank8IITM/AI-Cricket-Analytics-Project.git
cd AI-Cricket-Analytics-Project

# Install dependencies
pip install -r requirements.txt

# (Optional) set environment variables, e.g. for Gemini
# In a .env file or your environment:
# GEMINI_API_KEY=your_api_key_here

# Run the Streamlit app
streamlit run app.py
```
## Demo
Streamlit Link - https://ai-cricket-analytics-project.streamlit.app/ 

## 👨‍💻 Author

<div align="center">

### **Mayank Singh**
*AI & Data Science Enthusiast | IIT Madras*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/mayank-singh-398148294/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=for-the-badge&logo=github)](https://github.com/Mayank8IITM)
[![Email](https://img.shields.io/badge/Email-Contact-red?style=for-the-badge&logo=gmail)](mailto:mayanksingh.hfn@gmail.com)

</div>

<div align="center">
⭐ Star this repository if you find it helpful!
<br>Made with ❤️ for Cricket Analytics

</div> 
