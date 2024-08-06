@startuml AI-powered Customer Service Platform Workflow

skinparam sequenceArrowThickness 2
skinparam roundcorner 20
skinparam maxmessagesize 60

actor Customer
participant "NLP Chatbot" as Chatbot
participant "Sentiment Analysis" as Sentiment
participant "Ticket Router" as Router
participant "Knowledge Base" as KB
participant "AI Agent" as AI
participant "Human Agent" as Agent
participant "Analytics Engine" as Analytics

Customer -> Chatbot: Initiates conversation
activate Chatbot

Chatbot -> Sentiment: Analyze sentiment
activate Sentiment
Sentiment --> Chatbot: Sentiment score
deactivate Sentiment

Chatbot -> KB: Query knowledge base
activate KB
KB --> Chatbot: Relevant articles
deactivate KB

alt Simple query
    Chatbot --> Customer: Provide answer
else Complex query
    Chatbot -> Router: Create and route ticket
    activate Router
    Router -> AI: Assign to AI agent
    activate AI
    AI -> KB: Query for advanced info
    KB --> AI: Detailed information
    
    alt AI can resolve
        AI --> Customer: Provide solution
    else Needs human intervention
        AI -> Agent: Escalate to human agent
        activate Agent
        Agent --> Customer: Assist and resolve
        Agent -> KB: Update knowledge base
        deactivate Agent
    end
    deactivate AI
    deactivate Router
end

Chatbot -> Analytics: Log interaction data
activate Analytics
Analytics --> Chatbot: Update AI models
deactivate Analytics

Customer -> Chatbot: Provide feedback
Chatbot -> Analytics: Record feedback
activate Analytics
Analytics -> AI: Improve AI model
Analytics -> KB: Update knowledge base
deactivate Analytics

deactivate Chatbot

@enduml