# Lab 2: Building Your First Copilot

## 🎯 Objective

In this lab, you will learn how to build a functional copilot by creating custom topics, designing conversation flows, and implementing responses for common user queries.

## ⏱️ Estimated Time

45-60 minutes

## 📋 Prerequisites

- Completion of Lab 1: Getting Started with Copilot Studio
- Active copilot created in Copilot Studio
- Basic understanding of conversational design

## 🎓 What You'll Learn

- Creating custom topics
- Designing conversation flows
- Adding trigger phrases
- Creating bot responses
- Using question nodes
- Managing conversation paths
- Testing conversation flows

## 📝 Step-by-Step Instructions

### Step 1: Understanding Topics

Topics are the building blocks of your copilot. Each topic represents a specific conversation path about a particular subject.

**Key Concepts:**
- **Trigger phrases**: Words or sentences that activate a topic
- **Nodes**: Individual elements in a conversation flow
- **Messages**: Responses sent to users
- **Questions**: Prompts that gather information from users

### Step 2: Creating Your First Custom Topic

1. Open your copilot in Copilot Studio
2. In the left navigation, click on **"Topics"**
3. Click **"+ New topic"** and select **"From blank"**
4. Name your topic: "Store Hours"
5. Click **"Save"** in the top-right corner

**Expected Result:** A blank topic canvas appears, ready for you to build.

### Step 3: Adding Trigger Phrases

Trigger phrases help the copilot understand when to use this topic.

1. In the **"Trigger phrases"** section at the top, click **"Add"**
2. Add the following phrases (press Enter after each):
   - "What are your hours?"
   - "When are you open?"
   - "Store hours"
   - "Opening times"
   - "Are you open today?"

3. Click outside the text box to save

**Best Practice:** Add 5-10 varied trigger phrases to improve recognition accuracy.

### Step 4: Adding a Message Node

Now let's create a response when users ask about store hours.

1. Click the **"+"** button under the trigger phrases
2. Select **"Send a message"**
3. In the message box, type:
   ```
   Our store hours are:
   Monday - Friday: 9:00 AM - 8:00 PM
   Saturday: 10:00 AM - 6:00 PM
   Sunday: 12:00 PM - 5:00 PM
   ```
4. Click outside the message box to save

### Step 5: Testing Your Topic

1. Click **"Test your copilot"** in the bottom-left corner
2. Type: "What are your hours?"
3. Observe the response
4. Try other trigger phrases you added
5. Click **"Reset"** to start a new conversation

**Expected Result:** The copilot should respond with store hours information.

### Step 6: Creating a More Complex Topic with Questions

Let's create a topic that collects information from users.

1. Click **"Topics"** in the left navigation
2. Click **"+ New topic"** → **"From blank"**
3. Name it: "Product Inquiry"
4. Add trigger phrases:
   - "I need help with a product"
   - "Product information"
   - "Tell me about your products"
   - "What products do you have?"

### Step 7: Adding Question Nodes

Questions allow you to collect specific information from users.

1. Click the **"+"** button in your new topic
2. Select **"Ask a question"**
3. In the question field, type: "What type of product are you interested in?"
4. Under **"Identify"**, select **"User's entire response"**
5. In the **"Save response as"** field, name the variable: `ProductType`

### Step 8: Creating Conditional Responses

Based on the user's answer, provide different responses.

1. Click the **"+"** button under the question node
2. Select **"Add a condition"**
3. In the condition, select your variable `ProductType`
4. Click **"+"** to add conditions:
   - Condition 1: `ProductType` is equal to "electronics"
   - Condition 2: `ProductType` is equal to "clothing"
   - Add more as needed

### Step 9: Adding Responses for Each Condition

1. For the "electronics" branch:
   - Click **"+"** button
   - Select **"Send a message"**
   - Type: "Great! We have a wide range of electronics including laptops, smartphones, and tablets. Would you like specific recommendations?"

2. For the "clothing" branch:
   - Click **"+"** button
   - Select **"Send a message"**
   - Type: "Excellent! We offer clothing for men, women, and children. What category interests you?"

3. For the "All other conditions" branch:
   - Click **"+"** button
   - Select **"Send a message"**
   - Type: "I'd be happy to help! Could you please provide more details about what you're looking for?"

### Step 10: Adding Follow-up Options

Let's add quick reply options to guide the user.

1. After one of your message nodes, click **"+"**
2. Select **"Ask a question"**
3. Type: "Would you like to speak with a specialist?"
4. Under **"Identify"**, select **"Boolean"** (Yes/No)
5. Add user options:
   - "Yes, please"
   - "No, thank you"

### Step 11: Creating an End-of-Conversation Path

1. Under the "Yes" branch, add a message:
   ```
   Perfect! I'm connecting you with a specialist. Someone will be with you shortly.
   ```
2. Click **"+"** and select **"End conversation"** → **"Transfer to agent"**

3. Under the "No" branch, add a message:
   ```
   No problem! Feel free to ask if you need anything else. Have a great day!
   ```
4. Click **"+"** and select **"End conversation"** → **"End with survey"**

### Step 12: Comprehensive Testing

1. Open the test chat panel
2. Test the following scenarios:
   - Ask about store hours
   - Ask about products
   - Try different product types
   - Test the yes/no options
   - Verify all conversation paths work

3. Make note of any issues or improvements needed

## ✅ Success Criteria

You have successfully completed this lab if you can:
- [ ] Create custom topics from blank
- [ ] Add multiple trigger phrases
- [ ] Create message nodes with responses
- [ ] Add question nodes to collect information
- [ ] Implement conditional logic
- [ ] Create branching conversation paths
- [ ] Test complete conversation flows
- [ ] End conversations appropriately

## 🔍 Troubleshooting

**Issue**: Topic not triggering with certain phrases
- **Solution**: Add more varied trigger phrases. Ensure phrases are natural and diverse.

**Issue**: Variables not saving correctly
- **Solution**: Check variable names are unique and properly defined. Use the Variables panel to verify.

**Issue**: Conversation flow seems broken
- **Solution**: Check all nodes are properly connected. Look for red error indicators.

**Issue**: Test chat not responding
- **Solution**: Click "Reset" to restart. Ensure your topic is saved.

## 💡 Best Practices

1. **Trigger Phrases**: Add 5-10 varied phrases per topic
2. **Messages**: Keep responses clear and concise
3. **Questions**: Be specific about what information you need
4. **Conditions**: Cover all possible scenarios, including edge cases
5. **Testing**: Test every conversation path thoroughly
6. **User Experience**: Always provide clear next steps or options

## 🚀 Next Steps

Congratulations! You've built your first functional copilot. Continue to:
- [Lab 3: Working with Topics and Entities](../lab03-topics-and-entities/README.md)

## 📚 Additional Resources

- [Create and edit topics](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-create-edit-topics)
- [Use question nodes](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-ask-a-question)
- [Use conditions](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-using-conditions)
- [Test your copilot](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-test-bot)

## 💡 Key Takeaways

- Topics organize conversations around specific subjects
- Trigger phrases are crucial for topic recognition
- Question nodes enable information collection
- Conditional logic creates dynamic, personalized experiences
- Thorough testing ensures a smooth user experience

---

**Well done!** You've created a functional copilot with custom topics, questions, and conversation flows. You're ready to explore more advanced features.
