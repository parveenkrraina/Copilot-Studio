# Lab 5: Testing and Publishing Your Copilot

## 🎯 Objective

In this lab, you will learn comprehensive testing strategies, analytics monitoring, and how to publish your copilot to various channels for production use.

## ⏱️ Estimated Time

60-75 minutes

## 📋 Prerequisites

- Completion of Lab 4: Integrating with External Services
- A functional copilot with multiple topics
- Understanding of conversation flows and integrations
- Access to publish copilots in your environment

## 🎓 What You'll Learn

- Comprehensive testing strategies
- Using the test copilot panel effectively
- Tracking conversations with analytics
- Debugging common issues
- Publishing to different channels
- Monitoring copilot performance
- Iterative improvement based on metrics
- User acceptance testing

## 📝 Step-by-Step Instructions

### Step 1: Understanding Testing Phases

A complete testing strategy includes:
- **Unit Testing**: Individual topics and flows
- **Integration Testing**: Topic-to-topic navigation and flow calls
- **User Acceptance Testing**: Real user scenarios
- **Performance Testing**: Response times and reliability
- **Channel-Specific Testing**: Testing on deployment channels

### Step 2: Using the Test Copilot Panel

1. Open your copilot in Copilot Studio
2. Click **"Test your copilot"** in the bottom-left corner
3. Familiarize yourself with test panel features:
   - **Reset**: Starts a new conversation
   - **Track between topics**: Shows topic transitions
   - **Conversation tracking**: Displays which topic is active

### Step 3: Enable Detailed Tracking

1. In the test panel, click the **"Track between topics"** toggle at the top
2. This shows:
   - Which topic is currently active
   - When the conversation switches topics
   - Variables being set and their values

**Expected Result:** You can see the conversation flow in real-time.

### Step 4: Creating a Test Plan

Create a comprehensive test checklist:

```
Test Plan for [Your Copilot Name]

Topic: Greeting
- [ ] User says "Hello" → Greeting triggers
- [ ] User says "Hi there" → Greeting triggers
- [ ] Response is appropriate

Topic: Store Hours
- [ ] Trigger phrases work
- [ ] Correct hours are displayed
- [ ] Conversation ends gracefully

Topic: Book Appointment
- [ ] All required fields collect correctly
- [ ] Date validation works (no past dates)
- [ ] Email validation works
- [ ] Phone validation works
- [ ] Confirmation message displays all info

Topic: Product Inquiry
- [ ] Product type question works
- [ ] Conditional responses based on type
- [ ] Follow-up options work
- [ ] Transfer to agent works

Integration Tests
- [ ] Power Automate flow calls successfully
- [ ] Flow returns expected data
- [ ] Error handling works when flow fails
- [ ] Variables pass correctly to flows

Navigation Tests
- [ ] Topic redirection works
- [ ] Fallback topic triggers for unrecognized input
- [ ] Escalation to agent works
- [ ] Conversation can restart properly
```

### Step 5: Systematic Testing Execution

Execute each test in your plan:

1. **Reset** conversation between each test
2. Document results:
   - ✅ Pass
   - ❌ Fail (note the issue)
   - ⚠️ Partial (works but needs improvement)
3. Take screenshots of failures for debugging

### Step 6: Testing Edge Cases

Test scenarios users might not normally do:

1. **Empty inputs**: User presses enter without typing
2. **Unexpected inputs**: User types numbers when text is expected
3. **Very long inputs**: User types paragraphs
4. **Special characters**: User includes emojis, symbols
5. **Multiple questions**: User asks several things at once
6. **Context switching**: User changes topic mid-conversation
7. **Repeated inputs**: User says the same thing multiple times

Document how your copilot handles each scenario.

### Step 7: Testing Variable Persistence

1. Start a conversation, set some variables
2. Switch topics
3. Return to original topic
4. Verify variables are still available and correct

### Step 8: Testing Error Scenarios

Intentionally cause errors to test handling:

1. **Invalid dates**: Enter dates in wrong format
2. **Invalid emails**: Enter text that isn't an email
3. **Out of range numbers**: Test validation limits
4. **Flow failures**: Simulate by temporarily disabling a flow

Verify error messages are clear and helpful.

### Step 9: Accessing Analytics

1. In Copilot Studio, click **"Analytics"** in the left navigation
2. Explore available dashboards:
   - **Summary**: Overall performance metrics
   - **Customer Satisfaction**: CSAT scores
   - **Sessions**: Conversation details
   - **Topics**: Topic usage statistics

### Step 10: Understanding Key Metrics

Review and understand:

- **Total Sessions**: Number of conversations
- **Engagement Rate**: % of engaged vs. unengaged sessions
- **Resolution Rate**: % of conversations resolved without escalation
- **Abandon Rate**: % of conversations abandoned
- **CSAT Score**: Customer satisfaction rating
- **Top Topics**: Most frequently triggered topics

### Step 11: Analyzing Session Transcripts

1. In Analytics, go to **"Sessions"** tab
2. Click on a specific session to view the full transcript
3. Look for:
   - Where users get stuck
   - Unrecognized phrases
   - Topic trigger accuracy
   - Areas needing improvement

### Step 12: Improving Based on Analytics

Based on your analysis:

1. **Low-performing topics**: Add more trigger phrases
2. **High abandon rate**: Simplify or shorten conversations
3. **Unrecognized inputs**: Create new topics or add phrases
4. **Escalation patterns**: Improve automated responses

### Step 13: Preparing for Publishing

Before publishing, complete this checklist:

- [ ] All critical topics tested thoroughly
- [ ] Error handling implemented
- [ ] Analytics tracking enabled
- [ ] Fallback responses are helpful
- [ ] Escalation path works correctly
- [ ] CSAT survey configured
- [ ] Privacy and compliance reviewed
- [ ] Channel-specific requirements met

### Step 14: Publishing to Web Channel

1. Click **"Channels"** in the left navigation
2. Select **"Custom website"**
3. Click **"Copy"** to get the embed code
4. You'll see HTML code like:
```html
<iframe
    src="https://copilotstudio.microsoft.com/..."
    style="width: 400px; height: 600px;">
</iframe>
```
5. Paste this code into your website where you want the copilot to appear

### Step 15: Publishing to Microsoft Teams

1. In **"Channels"**, select **"Microsoft Teams"**
2. Click **"Turn on Teams"**
3. Choose availability:
   - For myself
   - For my team
   - For my organization
4. Click **"Submit for admin approval"** (if required)
5. Once approved, the copilot appears in Teams

**Testing in Teams:**
- Open Teams
- Find your copilot in the Apps section
- Test all functionalities in Teams context
- Verify formatting displays correctly

### Step 16: Publishing to Other Channels

Explore additional channels:

1. **Facebook Messenger**
   - Requires Facebook page
   - Configure in Channels → Facebook
   - Follow authentication steps

2. **Azure Bot Service Channels**
   - Slack
   - Telegram  
   - SMS (Twilio)
   - Others

3. **Mobile App**
   - Use Direct Line API
   - Implement in your mobile app

### Step 17: Configuring Authentication

For secure scenarios:

1. Go to **"Settings"** → **"Security"**
2. Choose authentication option:
   - **No authentication**: Public access
   - **Only for Teams**: Automatic Teams SSO
   - **Manual**: Azure AD or OAuth

3. Configure based on your security requirements

### Step 18: Setting Up Channel-Specific Features

Different channels support different features:

**Web Chat:**
- Custom colors and styling
- Adaptive cards
- File uploads

**Microsoft Teams:**
- Proactive messages
- Adaptive cards
- Integration with Teams features

**Test each channel separately** for optimal experience.

### Step 19: Monitoring Post-Launch

After publishing:

1. **Daily**: Check analytics for errors or spikes
2. **Weekly**: Review session transcripts
3. **Monthly**: Analyze trends and improvement areas
4. **Quarterly**: Major updates based on learnings

Set up alerts for:
- High abandon rates
- Increased escalations
- Error spikes

### Step 20: Continuous Improvement Cycle

Implement an ongoing improvement process:

1. **Collect Data**: Analytics, user feedback, transcripts
2. **Analyze**: Identify patterns and issues
3. **Prioritize**: Focus on high-impact improvements
4. **Implement**: Make iterative changes
5. **Test**: Verify improvements work
6. **Deploy**: Publish updates
7. **Monitor**: Track impact of changes
8. **Repeat**: Continuous cycle

### Step 21: Creating a Feedback Loop

Add a feedback topic:

1. Create topic: "Get User Feedback"
2. Ask: "How was your experience today? (1-5 stars)"
3. Ask: "What could we improve?"
4. Log to SharePoint or database via Power Automate
5. Review feedback regularly

### Step 22: Version Management

Best practices for managing versions:

1. **Test Environment**: Make changes here first
2. **Staging**: Deploy to staging for UAT
3. **Production**: Deploy only after thorough testing
4. **Rollback Plan**: Keep previous working version

Note: Use different environments in Power Platform for this.

### Step 23: Creating User Documentation

Prepare documentation for end users:

1. **Quick Start Guide**: How to interact with copilot
2. **FAQ**: Common questions and answers
3. **Feature List**: What the copilot can do
4. **Contact Info**: How to get help if copilot can't assist

### Step 24: Training Your Team

If others will maintain the copilot:

1. Document your design decisions
2. Create a maintenance guide
3. Train on updating topics
4. Train on reviewing analytics
5. Establish update procedures

## ✅ Success Criteria

You have successfully completed this lab if you can:
- [ ] Create and execute comprehensive test plans
- [ ] Use test panel with tracking enabled
- [ ] Test edge cases and error scenarios
- [ ] Access and understand analytics
- [ ] Publish copilot to at least one channel
- [ ] Configure channel-specific settings
- [ ] Set up monitoring and alerts
- [ ] Implement continuous improvement process

## 🔍 Troubleshooting

**Issue**: Copilot not appearing on website
- **Solution**: Check iframe code is correct. Verify domain is allowed in security settings.

**Issue**: Teams submission pending
- **Solution**: Contact your Teams admin. Approval required for org-wide deployment.

**Issue**: Analytics not showing data
- **Solution**: Ensure analytics are enabled. Data may take 24 hours to appear.

**Issue**: Performance issues on mobile
- **Solution**: Test specifically on mobile. Simplify complex responses. Reduce message length.

## 💡 Best Practices

1. **Testing**: Test thoroughly before each publish
2. **Analytics**: Review regularly, not just when issues arise
3. **User Feedback**: Actively collect and act on feedback
4. **Documentation**: Keep docs updated with each change
5. **Gradual Rollout**: Start with small user groups
6. **Monitoring**: Set up automated alerts for issues
7. **Version Control**: Document all changes
8. **Performance**: Monitor response times
9. **Accessibility**: Ensure copilot is accessible to all users
10. **Privacy**: Comply with data protection regulations

## 🚀 Next Steps

**Congratulations!** You've completed all five labs! You now have:
- A fully functional copilot
- Integration with external services
- Published to production channels
- Analytics and monitoring in place

**What's Next?**
- Explore advanced features (generative AI, multilingual support)
- Build specialized copilots for different departments
- Implement advanced authentication scenarios
- Create custom connectors for unique integrations

## 📚 Additional Resources

- [Test your copilot](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-test-bot)
- [Analytics in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/analytics-overview)
- [Publish your copilot](https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-fundamentals-publish-channels)
- [Configure channels](https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-connect-bot-to-web-channels)

## 💡 Key Takeaways

- Comprehensive testing prevents production issues
- Analytics provide valuable insights for improvement
- Different channels require specific considerations
- Continuous monitoring ensures ongoing quality
- User feedback drives meaningful improvements
- Documentation supports long-term success
- Iterative improvement is key to copilot excellence

---

**🎉 Congratulations!** You've completed the Copilot Studio Hands-On Labs! You now have the skills to build, test, deploy, and maintain professional-grade copilots. Keep learning and building amazing conversational experiences!
