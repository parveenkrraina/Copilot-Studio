
# Copilot Studio Topics: Triggers and Conversational Nodes Guide

## Overview
This lab demonstrates how to create and configure different types of topic triggers and conversational nodes in Microsoft Copilot Studio to build intelligent chatbot conversations.

## Learning Objectives
By the end of this lab, you will be able to:
- Create and configure different topic trigger types
- Implement various conversational nodes
- Build a complete customer service chatbot scenario
- Handle different conversation flows and user inputs

## Prerequisites
- Access to Microsoft Copilot Studio
- Basic understanding of conversational AI concepts

## Lab Scenario: Customer Service Chatbot
We'll build a customer service chatbot for "TechSupport Solutions" that handles:
- Product inquiries
- Technical support requests
- Order status checks
- Escalation to human agents

---

## Part 1: Understanding Topic Triggers

### Step 1: Create Your First Topic with Phrase Triggers

1. **Navigate to Copilot Studio**
    - Open Microsoft Copilot Studio
    - Select your copilot or create a new one

2. **Create a New Topic**
    - Click **Topics** in the left navigation
    - Select **+ New topic** → **From blank**
    - Name: `Product Inquiry`

3. **Configure Phrase Triggers**
    ```
    Trigger Phrases:
    - "I need help with a product"
    - "Tell me about your products"
    - "What products do you sell"
    - "Product information"
    - "Show me your catalog"
    ```

4. **Add Description**
    - Description: `Handles customer product inquiries and provides product information`

### Step 2: Create a Topic with Intent-Based Triggers

1. **Create New Topic**
    - Name: `Technical Support`
    - Description: `Provides technical support for customer issues`

2. **Configure Intent Triggers**
    ```
    Primary Intent: Technical Support
    
    Training Phrases:
    - "My device is not working"
    - "I'm having technical issues"
    - "Something is broken"
    - "Need tech support"
    - "Device troubleshooting"
    - "Error message appearing"
    ```

### Step 3: Create Event-Based Triggers

1. **Create New Topic**
    - Name: `Welcome Message`
    - Description: `Greets users when they start a conversation`

2. **Configure Event Trigger**
    - Trigger: **System** → **Conversation Start**
    - This topic will automatically trigger when users begin chatting

---

## Part 2: Implementing Conversational Nodes

### Step 4: Message Nodes - Building Welcome Flow

1. **In the Welcome Message Topic**
2. **Add Message Node**
    ```
    Welcome to TechSupport Solutions! 👋
    
    I'm here to help you with:
    • Product information
    • Technical support
    • Order status
    • Connect with an agent
    
    How can I assist you today?
    ```

### Step 5: Question Nodes - Gathering User Information

1. **In Product Inquiry Topic**
2. **Add Question Node**
    ```
    Question Type: Multiple Choice
    Question: "What type of product are you interested in?"
    
    Options:
    - Laptops
    - Smartphones
    - Accessories
    - Software
    ```

3. **Save Response to Variable**
    - Variable name: `ProductCategory`
    - This will store the user's selection

### Step 6: Condition Nodes - Creating Branched Logic

1. **Add Condition Node** after the question
2. **Configure Conditions**
    ```
    Condition 1: ProductCategory = "Laptops"
    → Action: Show laptop information
    
    Condition 2: ProductCategory = "Smartphones"
    → Action: Show smartphone information
    
    Condition 3: ProductCategory = "Accessories"
    → Action: Show accessories information
    
    Default: Show general product catalog
    ```

### Step 7: Advanced Question Types

1. **Create Order Status Topic**
2. **Add Text Input Question**
    ```
    Question: "Please provide your order number:"
    Entity: Text
    Variable: OrderNumber
    ```

3. **Add Number Input Question**
    ```
    Question: "What's your phone number for verification?"
    Entity: Number
    Variable: PhoneNumber
    ```

4. **Add Date/Time Question**
    ```
    Question: "When did you place this order?"
    Entity: Date and Time
    Variable: OrderDate
    ```