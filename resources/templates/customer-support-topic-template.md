# Sample Topic Template: Customer Support

This template provides a foundation for building a customer support topic in your copilot.

## Topic Name
Customer Support Request

## Description
Helps customers report issues and get support

## Trigger Phrases
- I need help
- I have a problem
- Something is not working
- Support request
- Technical issue
- Report a problem
- Get assistance

## Conversation Flow

### Step 1: Greeting
**Message:**
```
I'm sorry to hear you're experiencing an issue. I'm here to help! Let me gather some information to assist you better.
```

### Step 2: Collect Customer Information
**Question:** What is your name?
- **Entity:** Person Name
- **Variable:** `CustomerName`

**Question:** What is your email address?
- **Entity:** Email
- **Variable:** `CustomerEmail`

### Step 3: Issue Category
**Question:** What type of issue are you experiencing?
- **Entity:** Custom Entity - Issue Type
  - Technical Issue
  - Billing Question
  - Account Access
  - Product Information
  - Other
- **Variable:** `IssueCategory`

### Step 4: Conditional Logic - Technical Issue
**If** `IssueCategory` equals "Technical Issue":

**Question:** Can you describe the problem you're experiencing?
- **Entity:** User's entire response
- **Variable:** `TechnicalProblem`

**Question:** Have you tried restarting the application?
- **Entity:** Boolean (Yes/No)
- **Variable:** `HasRestarted`

**Condition:** If `HasRestarted` is No:
- **Message:** "Let's try restarting first. Please close and reopen the application, then let me know if the issue persists."
- **Action:** End conversation with survey

**Condition:** If `HasRestarted` is Yes:
- **Message:** "I understand. Let me create a support ticket for you."
- **Action:** Call Power Automate flow to create ticket

### Step 5: Conditional Logic - Billing Question
**If** `IssueCategory` equals "Billing Question":

**Question:** What is your billing concern?
- **Entity:** User's entire response
- **Variable:** `BillingConcern`

**Message:**
```
Thank you for explaining your billing concern. I'm connecting you with our billing department who can assist you better with this matter.
```
- **Action:** Transfer to agent (Billing team)

### Step 6: Conditional Logic - Account Access
**If** `IssueCategory` equals "Account Access":

**Question:** Are you unable to log in?
- **Entity:** Boolean
- **Variable:** `CannotLogin`

**Condition:** If `CannotLogin` is Yes:
- **Message:** "I can help with that. Would you like me to send a password reset link to your email?"
- **Question:** Confirm action
  - Entity: Boolean
  - Variable: `ConfirmReset`
- **Action:** If confirmed, call Power Automate flow to send reset email

### Step 7: Confirmation
**Message:**
```
Thank you, {CustomerName}! 

Here's a summary of your support request:
- Category: {IssueCategory}
- Email: {CustomerEmail}
- Ticket Number: {TicketNumber}

We'll get back to you within 24 hours. Is there anything else I can help you with?
```

**Question:** Need more help?
- **Entity:** Boolean
- **Variable:** `NeedMoreHelp`

**Condition:** If Yes, redirect to greeting
**Condition:** If No, end with satisfaction survey

## Variables Used
- `CustomerName` (Person Name)
- `CustomerEmail` (Email)
- `IssueCategory` (Custom Entity)
- `TechnicalProblem` (Text)
- `HasRestarted` (Boolean)
- `BillingConcern` (Text)
- `CannotLogin` (Boolean)
- `ConfirmReset` (Boolean)
- `TicketNumber` (Number - from Power Automate)
- `NeedMoreHelp` (Boolean)

## Power Automate Integrations

### Flow 1: Create Support Ticket
**Inputs:**
- CustomerName
- CustomerEmail
- IssueCategory
- IssueDescription

**Actions:**
1. Create item in SharePoint list "Support Tickets"
2. Send email notification to support team
3. Return ticket number

**Outputs:**
- TicketNumber
- ConfirmationMessage

### Flow 2: Send Password Reset
**Inputs:**
- CustomerEmail

**Actions:**
1. Validate email in system
2. Generate reset token
3. Send reset email
4. Log reset request

**Outputs:**
- ResetStatus
- Message

## Custom Entities Required

### Issue Type Entity
**Type:** Closed List
- Technical Issue
  - Synonyms: tech problem, software issue, app not working, bug
- Billing Question
  - Synonyms: payment, invoice, charge, subscription
- Account Access
  - Synonyms: login, password, access, credentials
- Product Information
  - Synonyms: features, how to, tutorial, guide
- Other
  - Synonyms: different, something else, not listed

## Escalation Rules
- If user retries answer more than 2 times → Transfer to agent
- If issue type is "Billing" → Transfer to billing team
- If user requests human agent → Transfer immediately
- If conversation exceeds 10 minutes → Offer transfer

## Success Metrics
- Resolution rate without escalation
- Average conversation duration
- Customer satisfaction score
- Ticket creation success rate

## Testing Scenarios
1. User with technical issue who has restarted
2. User with technical issue who hasn't restarted
3. User with billing question
4. User who can't log in and confirms reset
5. User who needs multiple types of help
6. User who provides invalid email
7. User who abandons conversation

## Notes
- Customize messages to match your brand voice
- Adjust escalation thresholds based on your team capacity
- Consider adding proactive messages if user waits
- Add authentication if handling sensitive information
- Regularly review analytics to optimize flow

---

**Usage Instructions:**
1. Copy this structure into a new topic
2. Customize messages for your brand
3. Create required custom entities
4. Build required Power Automate flows
5. Test thoroughly before publishing
