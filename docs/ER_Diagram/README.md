# AI Financial Advisor — ER Diagram

## Entities
- User
- Financial Profile
- Financial Analysis
- Goals
- AI Recommendations
- Chat History

## Primary Keys
- User: user_id
- Financial Profile: profile_id
- Financial Analysis: analysis_id
- Goals: goal_id
- AI Recommendations: recommendation_id
- Chat History: chat_id

## Foreign Keys
- Financial Profile: user_id
- Financial Analysis: user_id
- Goals: user_id
- AI Recommendations: user_id, analysis_id
- Chat History: user_id

## Relationships
- User → Financial Profile: 1:M
- User → Financial Analysis: 1:M
- User → Goals: 1:M
- User → Chat History: 1:M
- User → AI Recommendations: 1:M
- Financial Analysis → AI Recommendations: 1:M
## AIFA Entity Relationship Diagram

```mermaid
erDiagram
    USER ||--o{ FINANCIAL_PROFILE : has
    USER ||--o{ FINANCIAL_ANALYSIS : generates
    USER ||--o{ GOALS : creates
    USER ||--o{ CHAT_HISTORY : has
    USER ||--o{ AI_RECOMMENDATIONS : receives
    FINANCIAL_ANALYSIS ||--o{ AI_RECOMMENDATIONS : generates

    USER {
        int user_id PK
        varchar name
        varchar email
        varchar password
        datetime created_at
    }

    FINANCIAL_PROFILE {
        int profile_id PK
        int user_id FK
        decimal monthly_income
        decimal monthly_expenses
        decimal existing_savings
        decimal total_debt
        varchar risk_tolerance
        datetime created_at
        datetime updated_at
    }

    FINANCIAL_ANALYSIS {
        int analysis_id PK
        int user_id FK
        decimal savings_ratio
        decimal debt_ratio
        decimal emergency_fund
        decimal investment_capacity
        text analysis_data
        datetime created_at
    }

    GOALS {
        int goal_id PK
        int user_id FK
        varchar goal_name
        decimal target_amount
        int target_duration
        varchar priority_level
        datetime created_at
        datetime updated_at
    }

    AI_RECOMMENDATIONS {
        int recommendation_id PK
        int user_id FK
        int analysis_id FK
        int goal_id FK
        varchar recommendation_type
        text recommendation_text
        datetime generated_at
    }

    CHAT_HISTORY {
        int chat_id PK
        int user_id FK
        text user_query
        text ai_response
        datetime created_at
    }
```
