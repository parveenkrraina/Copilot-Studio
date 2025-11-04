# Lab 3: Working with Topics and Entities

## 🎯 Objective

In this lab, you will learn advanced topic management and how to use entities to extract and validate specific information from user inputs, creating more intelligent and context-aware conversations.

## ⏱️ Estimated Time

60-75 minutes

## 📋 Prerequisites

- Completion of Lab 2: Building Your First Copilot
- Understanding of basic topic creation
- Familiarity with conversation flows

## 🎓 What You'll Learn

- Understanding and using entities
- Pre-built vs. custom entities
- Creating custom entities
- Entity validation and error handling
- Managing topic redirects
- Using slot filling for data collection
- Advanced conversation management

## 📝 Step-by-Step Instructions

### Step 1: Understanding Entities

Entities are pre-defined information types that help extract structured data from user messages.

**Types of Entities:**
- **Pre-built entities**: Date, time, number, email, phone, currency, etc.
- **Custom entities**: Your own defined categories (e.g., product types, services)

### Step 2: Working with Pre-built Entities

Let's create a topic that uses pre-built entities to book an appointment.

1. Create a new topic: "Book Appointment"
2. Add trigger phrases:
   - "Book an appointment"
   - "Schedule a meeting"
   - "I need an appointment"
   - "Make a reservation"

### Step 3: Using Date and Time Entities

1. Add a question node: "What date would you like to schedule your appointment?"
2. Under **"Identify"**, select **"Date and time"**
3. Save response as: `AppointmentDate`
4. Enable **"Additional entity validation"**
5. In the validation field, add condition:
   - `AppointmentDate` is after `System.CurrentDate`
6. Add error message: "Please select a future date for your appointment."

**Expected Result:** Users must enter a valid future date.

### Step 4: Adding Time Selection

1. Add another question: "What time would you prefer?"
2. Under **"Identify"**, select **"Date and time"**
3. Save response as: `AppointmentTime`
4. Configure to recognize time only

### Step 5: Using Email Entity

1. Add question: "What is your email address for confirmation?"
2. Under **"Identify"**, select **"Email"**
3. Save response as: `CustomerEmail`
4. The copilot will automatically validate email format

### Step 6: Using Phone Number Entity

1. Add question: "What is your phone number?"
2. Under **"Identify"**, select **"Phone number"**
3. Save response as: `CustomerPhone`

### Step 7: Creating a Confirmation Message

Add a message node with all collected information:

```
Perfect! I've scheduled your appointment:

Date: {AppointmentDate}
Time: {AppointmentTime}
Email: {CustomerEmail}
Phone: {CustomerPhone}

You'll receive a confirmation email shortly.
```

**Note:** Use curly braces {} to insert variable values into messages.

### Step 8: Creating Custom Entities

Now let's create a custom entity for service types.

1. In the left navigation, click **"Entities"**
2. Click **"+ New entity"** → **"Closed list"**
3. Name it: "ServiceType"
4. Add list items:
   - **Item**: "Consultation", **Synonyms**: "consult, consultation, advice"
   - **Item**: "Repair", **Synonyms**: "fix, repair, service"
   - **Item**: "Installation", **Synonyms**: "install, installation, setup"
   - **Item**: "Maintenance", **Synonyms**: "maintain, maintenance, checkup"
5. Click **"Save"**

### Step 9: Using Custom Entities in Topics

1. Go back to your "Book Appointment" topic
2. Add a question at the beginning: "What type of service do you need?"
3. Under **"Identify"**, select your custom entity **"ServiceType"**
4. Save response as: `ServiceRequired`

### Step 10: Creating Service-Specific Responses

Add conditional logic based on the service type:

1. Add a condition node after the service question
2. Create branches:
   - If `ServiceRequired` is equal to "Consultation"
     - Message: "Great! Consultations typically take 30 minutes."
   - If `ServiceRequired` is equal to "Repair"
     - Message: "Understood. Repair services usually take 1-2 hours."
   - If `ServiceRequired` is equal to "Installation"
     - Message: "Perfect! Installation services can take 2-3 hours."
   - If `ServiceRequired` is equal to "Maintenance"
     - Message: "Noted. Maintenance checkups take about 1 hour."

### Step 11: Creating a Smart Entity (Optional)

Smart entities use AI to recognize patterns beyond predefined lists.

1. Click **"Entities"** → **"+ New entity"**
2. Select **"Smart entity"**
3. Name it: "ProductName"
4. Add description: "Recognizes product names from user input"
5. Add examples:
   - "I need help with my laptop"
   - "My smartphone isn't working"
   - "The tablet screen is cracked"
6. Click **"Save"**

### Step 12: Topic Redirection

Learn to redirect users between topics.

1. Create a new topic: "Check Appointment Status"
2. Add trigger phrases:
   - "Check my appointment"
   - "Appointment status"
   - "Do I have an appointment?"

3. Add a message: "I can help you check your appointment status."
4. Add a question: "Do you want to book a new appointment instead?"
5. Configure as Boolean (Yes/No)
6. For "Yes" branch:
   - Click **"+"** → **"Go to another topic"**
   - Select "Book Appointment" topic
7. For "No" branch:
   - Add message: "No problem. Your current appointments are displayed in your account."

### Step 13: Using Slot Filling

Slot filling allows collecting multiple pieces of information efficiently.

1. In your "Book Appointment" topic
2. Arrange questions in sequence
3. Enable **"Skip question if variable is already filled"** for each question
4. This allows users to provide information in any order

Example:
- User says: "Book appointment for tomorrow at 2 PM"
- Copilot recognizes date and time, skips those questions
- Only asks for remaining information (email, phone)

### Step 14: Entity Validation with Retry Logic

Add robust error handling:

1. In a question node with entity
2. Click on **"Additional entity validation"**
3. Set maximum retries: 2
4. Add retry message: "I didn't quite get that. Could you please try again?"
5. Add final error message: "I'm having trouble understanding. Let me connect you with an agent."
6. Add **"Transfer to agent"** node after max retries

### Step 15: Creating a Complex Multi-Entity Topic

Create a topic that handles order tracking:

1. New topic: "Track Order"
2. Trigger phrases:
   - "Track my order"
   - "Where is my package?"
   - "Order status"

3. Ask question: "What is your order number?"
   - Identify: Number
   - Save as: `OrderNumber`
   - Validation: Must be 6 digits

4. Ask question: "What email did you use for the order?"
   - Identify: Email
   - Save as: `OrderEmail`

5. Add message: "Let me check order #{OrderNumber} for {OrderEmail}..."

6. Add a condition:
   - Simulate order lookup (in real scenario, this would call an API)
   - Add message: "Your order is on its way! Expected delivery: [Date]"

### Step 16: Comprehensive Testing

Test all scenarios:
1. Valid inputs for all entities
2. Invalid dates (past dates)
3. Invalid email formats
4. Invalid phone numbers
5. Custom entity recognition with synonyms
6. Topic redirection
7. Slot filling with pre-filled information

## ✅ Success Criteria

You have successfully completed this lab if you can:
- [ ] Use pre-built entities (date, time, email, phone)
- [ ] Create custom closed list entities
- [ ] Implement entity validation
- [ ] Add error handling and retry logic
- [ ] Create entity-based conditional logic
- [ ] Redirect between topics
- [ ] Use slot filling for efficient data collection
- [ ] Test all entity validations

## 🔍 Troubleshooting

**Issue**: Entity not recognizing user input
- **Solution**: Add more synonyms to custom entities. Check for typos.

**Issue**: Date validation not working
- **Solution**: Ensure you're comparing with `System.CurrentDate`. Check condition syntax.

**Issue**: Variables not populating in messages
- **Solution**: Use correct syntax {VariableName}. Ensure variable names match exactly.

**Issue**: Topic redirect not working
- **Solution**: Verify the target topic exists and is published. Check redirect node configuration.

## 💡 Best Practices

1. **Entity Selection**: Choose the most specific entity type for your use case
2. **Validation**: Always validate critical information (dates, emails, phone numbers)
3. **Error Messages**: Provide clear, helpful error messages
4. **Synonyms**: Add comprehensive synonyms for custom entities
5. **Retry Logic**: Limit retries to 2-3 attempts before escalating
6. **User Experience**: Use slot filling to reduce repetitive questions
7. **Testing**: Test with various input formats and edge cases

## 🚀 Next Steps

Excellent work! You now understand entities and advanced topic management. Continue to:
- [Lab 4: Integrating with External Services](../lab04-integrations/README.md)

## 📚 Additional Resources

- [Use entities](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-entities-slot-filling)
- [Create custom entities](https://learn.microsoft.com/en-us/microsoft-copilot-studio/entities-custom)
- [Redirect to other topics](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-topic-management)
- [Entity validation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-variables)

## 💡 Key Takeaways

- Entities extract structured data from unstructured user input
- Pre-built entities handle common data types automatically
- Custom entities allow domain-specific data recognition
- Entity validation ensures data quality and user experience
- Topic redirection creates seamless conversation flows
- Slot filling improves efficiency by collecting information flexibly

---

**Fantastic progress!** You've mastered entities and advanced topic management. Your copilots can now handle complex data collection and validation scenarios.
