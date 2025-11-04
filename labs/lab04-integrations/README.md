# Lab 4: Integrating with External Services

## 🎯 Objective

In this lab, you will learn how to extend your copilot's capabilities by integrating with external services using Power Automate flows, connectors, and APIs to create dynamic, data-driven conversational experiences.

## ⏱️ Estimated Time

75-90 minutes

## 📋 Prerequisites

- Completion of Lab 3: Working with Topics and Entities
- Access to Power Automate
- Basic understanding of APIs and data flows
- Understanding of variables and entities

## 🎓 What You'll Learn

- Calling Power Automate flows from your copilot
- Using connectors to access external data
- Passing variables to flows
- Receiving and using flow responses
- Error handling for integrations
- Working with JSON responses
- Building dynamic responses from external data

## 📝 Step-by-Step Instructions

### Step 1: Understanding Integration Options

Copilot Studio can integrate with external services through:
- **Power Automate Flows**: Orchestrate multi-step processes
- **Connectors**: Pre-built integrations (SharePoint, SQL, etc.)
- **HTTP Requests**: Direct API calls
- **Skills**: Azure Bot Framework skills

### Step 2: Setting Up Power Automate

1. Open [Power Automate](https://flow.microsoft.com) in a new tab
2. Sign in with the same account used for Copilot Studio
3. Ensure you're in the same environment as your copilot
4. Familiarize yourself with the Power Automate interface

### Step 3: Creating Your First Flow for Copilot

Let's create a flow that retrieves weather information.

1. In Power Automate, click **"+ Create"**
2. Select **"Instant cloud flow"**
3. Name it: "Get Weather Information"
4. Under **"Choose how to trigger this flow"**, search for and select:
   **"Microsoft Copilot Studio"** (formerly Power Virtual Agents)
5. Click **"Create"**

**Expected Result:** A new flow with a Copilot Studio trigger is created.

### Step 4: Adding Input Parameters

1. In the trigger step, click **"Add an input"**
2. Select **"Text"**
3. Name it: `City`
4. Add a description: "The city name for weather lookup"
5. Click **"Add an input"** again
6. Select **"Text"**
7. Name it: `Country`
8. Add description: "Country code (e.g., US, UK)"

### Step 5: Adding an Action to Get Weather

For this example, we'll use a mock response (in production, you'd use a real weather API).

1. Click **"+ New step"**
2. Search for and select **"Compose"** action
3. In the Inputs field, create a JSON response:
```json
{
  "temperature": "72",
  "condition": "Sunny",
  "humidity": "45",
  "city": "@{triggerBody()['text']}"
}
```

**Note:** In a real scenario, you would use the **HTTP** action or a weather connector here.

### Step 6: Returning Values to Copilot

1. Click **"+ New step"**
2. Search for **"Return value(s) to Power Virtual Agents"** or **"Return value(s) to Copilot Studio"**
3. Click **"Add an output"**
4. Select **"Text"**
5. Name it: `Temperature`
6. Value: Select `temperature` from the Compose action dynamic content
7. Add another output:
   - Type: **Text**
   - Name: `Condition`
   - Value: Select `condition` from dynamic content
8. Add another output:
   - Type: **Text**
   - Name: `Humidity`
   - Value: Select `humidity` from dynamic content

9. Click **"Save"** at the top

### Step 7: Calling the Flow from Your Copilot

1. Return to Copilot Studio
2. Create a new topic: "Check Weather"
3. Add trigger phrases:
   - "What's the weather?"
   - "Tell me the weather"
   - "Weather forecast"
   - "How's the weather today?"

### Step 8: Adding Questions to Collect Data

1. Add a question: "Which city would you like to check?"
2. Identify: **City**
3. Save as: `UserCity`

4. Add another question: "What country? (Please use 2-letter code like US, UK, CA)"
5. Identify: **Text**
6. Save as: `UserCountry`

### Step 9: Calling Power Automate Flow

1. Click **"+"** button
2. Select **"Call an action"**
3. Find and select your flow: **"Get Weather Information"**
4. Map the inputs:
   - City: Select `UserCity` variable
   - Country: Select `UserCountry` variable

### Step 10: Using Flow Output

1. After the flow action node, click **"+"**
2. Select **"Send a message"**
3. Create a response using the flow outputs:
```
Here's the current weather in {UserCity}:

Temperature: {Temperature}°F
Condition: {Condition}
Humidity: {Humidity}%

Have a great day!
```

### Step 11: Testing the Integration

1. Open the test chat
2. Type: "What's the weather?"
3. When prompted, enter: "Seattle"
4. When prompted for country, enter: "US"
5. Verify the weather information is displayed

**Expected Result:** The copilot retrieves and displays weather information.

### Step 12: Creating a SharePoint Integration

Let's create a flow that logs customer feedback to SharePoint.

1. In Power Automate, create a new instant cloud flow
2. Name it: "Log Customer Feedback"
3. Select **"Microsoft Copilot Studio"** trigger

4. Add inputs:
   - Text: `CustomerName`
   - Text: `FeedbackText`
   - Text: `Rating`

5. Add action: **"SharePoint - Create item"**
6. Configure:
   - Site Address: Select your SharePoint site
   - List Name: "Customer Feedback" (you'll need to create this list first)
   - Map fields:
     - Title: `CustomerName`
     - Feedback: `FeedbackText`
     - Rating: `Rating`

7. Add **"Return value(s)"** action
   - Text output: `ConfirmationMessage`
   - Value: "Your feedback has been recorded. Thank you!"

8. Save the flow

### Step 13: Creating Feedback Topic in Copilot

1. Create new topic: "Submit Feedback"
2. Add trigger phrases:
   - "I want to give feedback"
   - "Submit feedback"
   - "Leave a review"

3. Add questions:
   - "What is your name?"
     - Identify: Person Name
     - Save as: `CustomerName`
   
   - "Please share your feedback:"
     - Identify: User's entire response
     - Save as: `FeedbackText`
   
   - "How would you rate your experience? (1-5)"
     - Identify: Number
     - Save as: `Rating`
     - Validation: Between 1 and 5

4. Call the "Log Customer Feedback" flow
5. Display the confirmation message

### Step 14: Working with HTTP Requests

For direct API calls, use the HTTP action in Power Automate.

1. Create a new flow: "Get Product Information"
2. Add Copilot Studio trigger with input:
   - Text: `ProductID`

3. Add **"HTTP"** action
4. Configure:
   - Method: GET
   - URI: `https://api.example.com/products/{ProductID}`
   - Headers: 
     - Content-Type: application/json
     - Authorization: Bearer YOUR_API_KEY

5. Add **"Parse JSON"** action to process the response
6. Return parsed values to the copilot

### Step 15: Error Handling in Flows

Add robust error handling to your flows:

1. In your flow, click the **"..."** menu on any action
2. Select **"Configure run after"**
3. Check: **"has failed"** and **"has timed out"**
4. Add a **"Compose"** action after failures
5. Create an error message:
```json
{
  "status": "error",
  "message": "Unable to retrieve information. Please try again later."
}
```

6. Return this as an output
7. In your copilot topic, check for error status and display appropriate message

### Step 16: Using Variables Across Multiple Flows

Create a data collection topic that calls multiple flows:

1. Topic: "Customer Onboarding"
2. Collect customer information (name, email, company)
3. Call Flow 1: "Create Customer Record" → Returns CustomerID
4. Use CustomerID in Flow 2: "Send Welcome Email"
5. Call Flow 3: "Add to Mailing List"
6. Display confirmation with all relevant information

### Step 17: Advanced: Conditional Flow Calls

Add logic to call different flows based on conditions:

1. In your topic, add a condition based on user input
2. Branch 1: Call "Premium Service Flow"
3. Branch 2: Call "Standard Service Flow"
4. Handle responses from different flows appropriately

## ✅ Success Criteria

You have successfully completed this lab if you can:
- [ ] Create Power Automate flows triggered by Copilot Studio
- [ ] Pass variables from copilot to flows
- [ ] Receive and use flow outputs in copilot responses
- [ ] Integrate with SharePoint or other connectors
- [ ] Make HTTP API calls through flows
- [ ] Implement error handling for integrations
- [ ] Test complete integration scenarios

## 🔍 Troubleshooting

**Issue**: Flow not appearing in copilot
- **Solution**: Ensure flow is saved and uses Copilot Studio trigger. Check environment consistency.

**Issue**: Variables not passing to flow
- **Solution**: Verify variable names match exactly. Check variable types (text, number, etc.).

**Issue**: Flow returns error
- **Solution**: Test flow independently in Power Automate. Check API keys and permissions.

**Issue**: Timeout errors
- **Solution**: Optimize flow performance. Consider asynchronous processing for long operations.

**Issue**: Permission errors
- **Solution**: Ensure proper permissions for connectors and data sources.

## 💡 Best Practices

1. **Flow Design**: Keep flows focused on single responsibilities
2. **Error Handling**: Always implement comprehensive error handling
3. **Testing**: Test flows independently before integrating with copilot
4. **Performance**: Minimize API calls and optimize data retrieval
5. **Security**: Never expose API keys in copilot responses
6. **Naming**: Use clear, descriptive names for flows and variables
7. **Documentation**: Document flow purposes and expected inputs/outputs
8. **Monitoring**: Regularly check flow run history for failures

## 🚀 Next Steps

Excellent! You've mastered integrations. Now proceed to:
- [Lab 5: Testing and Publishing Your Copilot](../lab05-testing-and-publishing/README.md)

## 📚 Additional Resources

- [Use Power Automate flows](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-flow)
- [Create flows for copilots](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-create-flow)
- [Power Automate connectors](https://learn.microsoft.com/en-us/connectors/)
- [HTTP actions in Power Automate](https://learn.microsoft.com/en-us/power-automate/http-action)

## 💡 Key Takeaways

- Power Automate extends copilot capabilities significantly
- Flows enable integration with hundreds of services
- Proper error handling ensures reliable user experiences
- Variables seamlessly pass between copilots and flows
- Testing integrations independently simplifies debugging
- External data creates dynamic, personalized conversations

---

**Outstanding work!** Your copilot can now interact with external services, access real-time data, and provide dynamic responses. You're ready for the final lab on testing and publishing.
