@startuml AI-powered Customer Service Platform - System Context

!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Context.puml

LAYOUT_WITH_LEGEND()

title System Context diagram for AI-powered Customer Service Platform

Person(customer, "Customer", "A user seeking support or information")

System_Boundary(ai_platform, "AI-powered Customer Service Platform") {
    System(chatbot, "NLP Chatbot", "Handles customer interactions")
    System(sentiment, "Sentiment Analysis", "Analyzes customer sentiment")
    System(router, "Ticket Router", "Routes complex queries")
    System(kb, "Knowledge Base", "Stores and retrieves information")
    System(ai_agent, "AI Agent", "Handles complex queries")
    System(analytics, "Analytics Engine", "Logs and analyzes interactions")
}

Person(human_agent, "Human Agent", "Handles escalated queries")

Rel(customer, chatbot, "Interacts with")
Rel(chatbot, sentiment, "Analyzes sentiment")
Rel(chatbot, kb, "Queries")
Rel(chatbot, router, "Routes complex queries")
Rel(router, ai_agent, "Assigns tickets")
Rel(ai_agent, kb, "Queries for advanced info")
Rel(ai_agent, human_agent, "Escalates to")
Rel(human_agent, customer, "Assists")
Rel(human_agent, kb, "Updates")
Rel(chatbot, analytics, "Logs interaction data")
Rel(analytics, chatbot, "Updates AI models")
Rel(analytics, ai_agent, "Improves AI model")
Rel(analytics, kb, "Updates")

@enduml