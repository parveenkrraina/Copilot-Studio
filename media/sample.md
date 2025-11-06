
# End-to-End Copilot Studio Automation Solution

## Case Study: Customer Support Automation for E-Commerce Platform

### Problem Statement
**Contoso Electronics** is an e-commerce company facing challenges with customer support:
- **High Volume**: Receiving 500+ daily customer inquiries about order status, product information, and returns
- **Response Time**: Average response time is 4-6 hours, leading to customer dissatisfaction
- **Resource Constraint**: Support team of 5 agents is overwhelmed and unable to scale during peak seasons
- **Knowledge Scattered**: Product information, return policies, and FAQs are spread across multiple documents
- **Order Tracking**: Customers repeatedly ask "Where is my order?" requiring manual lookup in backend systems

### Business Impact
- Customer satisfaction score: 3.2/5
- 30% of tickets are repetitive questions
- Support cost: $15,000/month
- Lost revenue due to poor customer experience: Estimated $25,000/month

### Solution Overview
We will build an intelligent **Customer Support Copilot** using Microsoft Copilot Studio that will:
1. **Automate responses** to common inquiries (order status, product info, return policy)
2. **Integrate with backend systems** to fetch real-time order information
3. **Provide 24/7 support** with consistent, accurate responses
4. **Escalate complex issues** to human agents when needed
5. **Learn from interactions** to improve over time

### Expected Outcomes
- Reduce response time from 4-6 hours to < 2 minutes for common queries
- Handle 70% of inquiries automatically
- Reduce support costs by 40%
- Improve customer satisfaction to 4.5/5
- Free up human agents for complex issues

---

## Prerequisites

### Software Requirements
- **Microsoft 365 Account** with appropriate licenses (Copilot Studio license required)
- **Power Platform Environment** with Dataverse enabled
- **Web Browser**: Microsoft Edge or Google Chrome (latest version)
- **Access Rights**: Environment Maker role or higher in Power Platform

### Technical Prerequisites
- **Azure Subscription** (for backend API integration, if needed)
- **Sample Order Database** or API endpoint (we'll create a mock service)
- **Knowledge Base Documents**: FAQs, product catalogs, return policies

### Required Files (Create in Repository Structure)
```
/allfiles
    /knowledge-base
        - faq.docx
        - return-policy.pdf
        - product-catalog.xlsx
    /data
        - sample-orders.json
        - customer-profiles.json
    /integrations
        - order-api-spec.json
```

---

## Step-by-Step Implementation Guide

### Phase 1: Environment Setup

#### Step 1.1: Access Copilot Studio
1. Open your web browser (Microsoft Edge or Chrome)
2. Navigate to **https://copilotstudio.microsoft.com**
3. Sign in with your Microsoft 365 credentials
4. Click **Sign in** button on the top right corner
5. If prompted, select your organization account
6. Wait for the Copilot Studio dashboard to load (may take 10-15 seconds)

#### Step 1.2: Select or Create Environment
1. On the Copilot Studio home page, look at the top right corner for the **Environment** dropdown
2. Click the **Environment** dropdown menu
3. Review the list of available environments
4. **Option A - Use Existing Environment:**
     - Select an environment where you have Environment Maker or System Administrator permissions
5. **Option B - Create New Environment (if you have admin rights):**
     - Click **+ New environment** at the bottom of the dropdown
     - Enter environment name: `Contoso-Support-Production`
     - Select Region: Choose your closest region (e.g., United States)
     - Select Environment type: **Production**
     - Enable **Add a Dataverse data store**: Toggle to **Yes**
     - Click **Next**
     - Review settings and click **Save**
     - Wait 2-3 minutes for environment provisioning

#### Step 1.3: Create New Copilot
1. From Copilot Studio home page, click **+ Create** button on the left navigation panel
2. Select **New copilot** tile
3. On the "Create a copilot" page, choose **Skip to configure**
4. Fill in the copilot details:
     - **Name**: `Contoso Customer Support Bot`
     - **Description**: `Intelligent customer support assistant for order tracking, product information, and general inquiries`
     - **Instructions**: Enter the following:
         ```
         You are a helpful customer support assistant for Contoso Electronics. 
         Your role is to help customers with:
         - Order status and tracking
         - Product information and recommendations
         - Return and refund policies
         - General FAQs
         
         Always be polite, professional, and concise. 
         If you cannot answer a question, offer to escalate to a human agent.
         Use the customer's name when available to personalize interactions.
         ```
     - **Language**: Select `English`
5. Click **Create** button at the top right
6. Wait 30-60 seconds for the copilot to be created
7. You will be redirected to the copilot **Overview** page

---

### Phase 2: Configure Knowledge Base

#### Step 2.1: Prepare Knowledge Documents
1. Create the following documents on your local machine in folder: `D:/OneDrive - VNode ITeS/Documents/GitHub/Copilot-Studio/allfiles/knowledge-base/`

**File 1: faq.docx** (Create in Microsoft Word)
```
FREQUENTLY ASKED QUESTIONS

Q: What are your shipping options?
A: We offer Standard Shipping (5-7 business days, FREE on orders over $50), Express Shipping (2-3 business days, $15), and Overnight Shipping (1 business day, $30).

Q: How can I track my order?
A: Once your order ships, you'll receive a tracking number via email. You can also check your order status by logging into your account or asking our support bot.

Q: What is your return policy?
A: We accept returns within 30 days of delivery for most items. Products must be unused and in original packaging. Refunds are processed within 5-7 business days.

Q: Do you ship internationally?
A: Yes, we ship to over 50 countries. International shipping costs and delivery times vary by destination.

Q: How do I cancel my order?
A: Orders can be cancelled within 1 hour of placement. After that, please contact our support team for assistance.

Q: What payment methods do you accept?
A: We accept Visa, Mastercard, American Express, PayPal, Apple Pay, and Google Pay.

Q: How do I contact customer support?
A: You can reach us via live chat on our website, email at support@contoso-electronics.com, or phone at 1-800-CONTOSO (9 AM - 9 PM EST).

Q: Do you offer warranty on products?
A: All products come with manufacturer's warranty. Extended warranty options are available at checkout.
```

**File 2: return-policy.pdf** (Create in Word, save as PDF)
```
CONTOSO ELECTRONICS RETURN POLICY

30-Day Return Window
- Returns accepted within 30 days of delivery date
- Products must be unused, undamaged, and in original packaging
- Original receipt or order confirmation required

Non-Returnable Items
- Downloadable software and digital products
- Personalized or custom-made items
- Perishable goods
- Gift cards and promotional items
- Items marked as "Final Sale"

Return Process
1. Log into your account on contoso-electronics.com
2. Navigate to "Orders" and select the item to return
3. Click "Request Return" and select reason
4. Print the prepaid return label
5. Package item securely with all original accessories
6. Drop off at any authorized carrier location

Refund Processing
- Refunds issued within 5-7 business days after receiving returned item
- Original payment method will be credited
- Shipping charges are non-refundable (except defective items)
- Return shipping is FREE for defective/damaged items

Exchanges
- Exchange requests processed same as returns
- New item ships once return is received and processed
- Price difference may apply

Contact Us
For return questions: returns@contoso-electronics.com
Phone: 1-800-CONTOSO, Option 2
```

**File 3: product-catalog.xlsx** (Create in Excel)
| Product ID | Product Name | Category | Price | Stock Status | Features |
|------------|--------------|----------|-------|--------------|----------|
| PROD001 | Wireless Headphones Pro | Audio | $199.99 | In Stock | Noise cancellation, 30hr battery, Bluetooth 5.0 |
| PROD002 | Smart Watch Elite | Wearables | $299.99 | In Stock | Heart rate monitor, GPS, 5-day battery |
| PROD003 | 4K Ultra HD TV 55" | TV & Video | $699.99 | Limited Stock | HDR10+, Smart TV, 120Hz refresh rate |
| PROD004 | Laptop Pro 15 | Computers | $1299.99 | In Stock | Intel i7, 16GB RAM, 512GB SSD |
| PROD005 | Wireless Mouse | Accessories | $49.99 | In Stock | Ergonomic, 1600 DPI, USB-C charging |

#### Step 2.2: Upload Knowledge Sources
1. In your copilot, click **Knowledge** in the left navigation panel
2. Click **+ Add knowledge** button
3. Select **Files** from the dropdown options
4. Click **Upload** button
5. In the file picker dialog, navigate to: `D:/OneDrive - VNode ITeS/Documents/GitHub/Copilot-Studio/allfiles/knowledge-base/`
6. Select `faq.docx`, hold Ctrl key, select `return-policy.pdf`
7. Click **Open** button
8. Wait for upload progress bar to complete (10-30 seconds per file)
9. You will see confirmation: "2 files uploaded successfully"
10. Click **Add** button at the bottom right
11. Wait for indexing to complete (status changes from "Processing" to "Ready" - takes 1-2 minutes)

#### Step 2.3: Add Website as Knowledge Source (Optional)
1. Still on the **Knowledge** page, click **+ Add knowledge** again
2. Select **Public websites** from dropdown
3. Enter website URL: `https://www.microsoft.com/en-us/surface` (use your actual company URL or a demo site)
4. Click **Add** button
5. Wait for crawling to complete (2-5 minutes, status shows "Crawling...")

#### Step 2.4: Verify Knowledge Sources
1. On the **Knowledge** page, verify you see all added sources in the list
2. Each source should show status: **Ready** (green checkmark icon)
3. Click on each knowledge source to preview the content
4. Click **X** or **Close** to return to list

---

### Phase 3: Create Topics for Common Scenarios

#### Step 3.1: Create "Check Order Status" Topic
1. Click **Topics** in the left navigation panel
2. Click **+ Add a topic** button at the top
3. Select **From blank** option
4. Click **From blank** card that appears
5. In the topic editor:
     - **Topic name field** (top of page): Enter `Check Order Status`
     - **Description field**: Enter `Helps customers track their order by order number`

6. **Configure Trigger Phrases:**
     - In the **Trigger** node, click **Edit** under "Phrases"
     - Click **+ Add** to add trigger phrases one by one:
         - `Where is my order`
         - `Track my order`
         - `Order status`
         - `Check order`
         - `Track package`
         - `Shipping status`
     - Click **Save** after adding all phrases

7. **Add Greeting Message Node:**
     - Below the Trigger node, click the **+** icon
     - Select **Send a message**
     - In the message box, type:
         ```
         I'll help you track your order. I'll need your order number to look this up.
         ```
     - Click outside the message box to confirm

8. **Add Question Node to Collect Order Number:**
     - Click the **+** icon below the message node
     - Select **Ask a question**
     - In "Enter a message" field, type:
         ```
         Please enter your order number (format: ORD-XXXXX):
         ```
     - In **Identify** dropdown, select **User's entire response**
     - Under **Save response as**, the variable name will auto-populate
     - Click the variable name and change it to: `OrderNumber`
     - Click **Save** or click outside the node

9. **Add Condition Node to Validate Order Number:**
     - Click **+** icon below the question node
     - Select **Add a condition**
     - Click **Select a variable** in the condition
     - Select the `OrderNumber` variable
     - Change condition operator to **contains**
     - In the value field, enter: `ORD-`
     - This creates condition: `OrderNumber contains ORD-`

10. **Add Success Path (Condition Met):**
        - Under the **Condition Met** branch, click **+** icon
        - Select **Send a message**
        - Enter message:
            ```
            Thank you! Let me look up order {OrderNumber} for you.
            
            [This is where we'll integrate with the order API in Phase 4]
            
            Your order is currently: IN TRANSIT
            Expected delivery: 2 business days
            
            Would you like tracking details sent to your email?
            ```
        - Click outside message box

11. **Add Failure Path (Condition Not Met):**
        - Under the **All Other Conditions** branch, click **+** icon
        - Select **Send a message**
        - Enter message:
            ```
            The order number format doesn't look right. Order numbers start with "ORD-" followed by 5 digits.
            
            You can find your order number in your confirmation email or account order history.
            
            Would you like me to help you with something else?
            ```

12. **Save the Topic:**
        - Click **Save** button at the top right
        - Wait for "Saved successfully" notification

#### Step 3.2: Create "Product Information" Topic
1. On the **Topics** page, click **+ Add a topic**
2. Select **From blank**
3. **Configure Topic:**
     - **Name**: `Product Information`
     - **Description**: `Provides details about products, availability, and specifications`

4. **Add Trigger Phrases:**
     - In Trigger node, click **Edit**
     - Add phrases:
         - `Tell me about products`
         - `Product details`
         - `What products do you have`
         - `Product information`
         - `Show me products`
         - `Product catalog`
     - Click **Save**

5. **Add Initial Message:**
     - Click **+** below trigger
     - Select **Send a message**
     - Message text:
         ```
         I can help you find information about our products. What type of product are you interested in?
         ```

6. **Add Multiple Choice Question:**
     - Click **+** below message
     - Select **Ask a question**
     - Message: `Please select a category:`
     - In **Identify** dropdown, select **Multiple choice options**
     - Add options (click **+ New option** for each):
         - Option 1: `Audio` (Display text) | `audio` (submit value)
         - Option 2: `Wearables` | `wearables`
         - Option 3: `TV & Video` | `tv`
         - Option 4: `Computers` | `computers`
         - Option 5: `Accessories` | `accessories`
     - **Save response as**: Change variable name to `ProductCategory`

7. **Add Condition Branches for Each Category:**
     - Click **+** below question node
     - Select **Add a condition**
     - Create multiple conditions:
         - **Condition 1**: `ProductCategory is equal to audio`
             - Add message node:
                 ```
                 Here are our Audio products:
                 
                 🎧 Wireless Headphones Pro - $199.99
                 - Features: Noise cancellation, 30hr battery, Bluetooth 5.0
                 - Status: In Stock
                 
                 Would you like more details on any specific product?
                 ```
         - Click **+ Add condition** to add more branches
         - **Condition 2**: `ProductCategory is equal to computers`
             - Add message:
                 ```
                 Here are our Computer products:
                 
                 💻 Laptop Pro 15 - $1,299.99
                 - Intel i7 processor, 16GB RAM, 512GB SSD
                 - Status: In Stock
                 
                 Need help choosing the right model?
                 ```
         - Continue for remaining categories (wearables, tv, accessories)

8. **Save Topic:**
     - Click **Save** at top right

#### Step 3.3: Create "Return Request" Topic
1. Click **+ Add a topic** → **From blank**
2. **Configure:**
     - **Name**: `Return Request`
     - **Description**: `Guides customers through return process`

3. **Add Triggers:**
     - `I want to return`
     - `Return item`
     - `Refund request`
     - `How do I return`
     - `Start a return`

4. **Build Conversation Flow:**
     - **Node 1 - Message**: `I'll help you with your return. Our return policy allows returns within 30 days of delivery.`
     - **Node 2 - Question**: 
         - Ask: `Do you have your order number?`
         - Identify: **Multiple choice**
         - Options: `Yes` | `No`
         - Save as: `HasOrderNumber`
     
     - **Node 3 - Condition**: `If HasOrderNumber equals Yes`
         - **Branch 1 (Yes)**:
             - Ask question: `Please enter your order number:`
             - Identify: **User's entire response**
             - Save as: `ReturnOrderNumber`
             - Message: `Thank you. To process your return:\n\n1. Log into your account\n2. Go to Orders section\n3. Select order {ReturnOrderNumber}\n4. Click "Request Return"\n5. Print prepaid label\n\nRefunds process in 5-7 days. Need more help?`
         
         - **Branch 2 (No)**:
             - Message: `No problem! You can find your order number in your confirmation email or by logging into your account. Once you have it, I can help you start the return process.`

5. **Save Topic**

---

### Phase 4: Integrate Power Automate Flow for Order API

#### Step 4.1: Create Mock Order API Data (Using Cloud Flow)
1. From Copilot Studio, click **Topics** in navigation
2. Open the **Check Order Status** topic you created earlier
3. Find the message node where you wrote "[This is where we'll integrate with the order API]"
4. Click the **+** icon just before this message node
5. Select **Call an action**
6. Click **Create a flow** button

7. **Power Automate opens in new tab:**
     - You'll see a flow template with:
         - Trigger: **Copilot Studio (Preview)**
         - Default action nodes
     
8. **Configure Flow Inputs:**
     - Click on the trigger node **Copilot Studio**
     - Click **+ Add an input**
     - Select **Text**
     - Input name: `OrderNumber`
     - Click **+ Add an input** again
     - Select **Text**
     - Input name: `CustomerEmail`

9. **Add Compose Action to Simulate API Response:**
     - Click **+** between trigger and "Return value(s) to Copilot Studio"
     - Search for and select **Compose** (Data Operations)
     - In the **Inputs** field, click and enter following JSON:
         ```json
         {
             "orderId": "@{triggerBody()?['text']}",
             "status": "In Transit",
             "estimatedDelivery": "2 business days",
             "trackingNumber": "1Z999AA1012345678",
             "carrier": "UPS",
             "shippingAddress": "123 Main St, Seattle, WA 98101",
             "items": [
                 {
                     "productName": "Wireless Headphones Pro",
                     "quantity": 1,
                     "price": 199.99
                 }
             ],
             "orderTotal": 199.99,
             "orderDate": "2024-01-15"
         }
         ```
     - Note: Click "Dynamic content" button and select `OrderNumber` from trigger to replace the @{triggerBody()?['text']} portion

10. **Configure Output to Copilot:**
        - Click on **Return value(s) to Copilot Studio** node
        - Click **+ Add an output**
        - Select **Text**
        - Title: `OrderStatus`
        - Value: Click in field, then click **Dynamic content** button, select **Outputs** from Compose action
        - Click **+ Add an output** again
        - Select **Text**
        - Title: `TrackingNumber`
        - Value: Enter `1Z999AA1012345678` (or use expression to extract from Compose output)

11. **Save and Name Flow:**
        - At top left, click on flow name "Untitled"
        - Rename to: `Get Order Status - Contoso`
        - Click **Save** button at top right
        - Wait for "Your flow is ready" message
        - Click **<- Back** arrow to return to Copilot Studio

#### Step 4.2: Connect Flow to Topic
1. Back in Copilot Studio, you should still be in the **Check Order Status** topic
2. At the action node you just added, you should now see **Get Order Status - Contoso** flow
3. If not visible, click **Refresh** and select the flow from dropdown
4. **Map Inputs:**
     - Click **OrderNumber** input field
     - Select variable `{OrderNumber}` from the variable picker
     - Click **CustomerEmail** input field
     - Type a test email: `customer@contoso.com` or leave blank

5. **Update Success Message with Flow Output:**
     - Find or create the message node below the flow action
     - Edit the message to use flow outputs:
         ```
         Great news! I found your order.
         
         📦 Order Number: {OrderNumber}
         📍 Status: {Topic.OrderStatus}
         🚚 Tracking: {Topic.TrackingNumber}
         📅 Estimated Delivery: 2 business days
         
         Your package is on its way! You can track it using the tracking number above.
         
         Is there anything else I can help you with?
         ```
     - To add variables: Click **{x}** icon in message editor and select outputs from the flow

6. **Save Topic:** Click **Save** button

---

### Phase 5: Create and Configure Agent (Copilot Agent)

#### Step 5.1: Enable Generative Answers
1. In your copilot, click **Settings** (gear icon) in top right
2. In the settings panel, select **Generative AI** tab
3. Under **Generative answers**, toggle switch to **On**
4. Configure options:
     - **Content moderation**: Set to **Medium**
     - **Data sources**: Verify your knowledge sources are listed
     - **Response length**: Select **Medium** (100-150 words)
5. Click **Save** at bottom of settings panel
6. Click **X** to close settings

#### Step 5.2: Configure Boosted Conversations
1. Click **Settings** gear icon again
2. Select **Generative AI** tab
3. Scroll to **Generative Conversations** section
4. Toggle **Enable generative conversations** to **On**
5. Under this setting, configure:
     - **Allow copilot to invoke topics**: Toggle **On**
     - **Allow copilot to use connectors**: Toggle **On**
6. In **Instructions** text box, add:
     ```
     When a customer asks about orders, products, or returns:
     - Always check if there's a specific topic that handles this request
     - Invoke the appropriate topic to provide accurate, structured responses
     - Use knowledge sources for general questions
     - Be concise and action-oriented
     - Always offer to escalate to human agent if the issue is complex
     ```
7. Click **Save**


#### Step 5.3: Configure Copilot Orchestration Settings
1. Click **Settings** (gear icon) in top right corner
2. Select **AI Capabilities** tab from the left panel in settings
3. Under **Orchestration** section, review the copilot behavior options:
     - **How should your copilot decide how to respond?**: Keep default **Generative** selected
     - This enables the copilot to intelligently decide when to use topics, knowledge sources, or generative answers
4. Scroll to **Generative AI** section
5. Review the **Generative answers** configuration:
     - Ensure toggle is **On**
     - **Content moderation**: Verify set to **Medium**
     - This controls how the copilot generates responses from your knowledge sources
6. Click **Save** at the bottom

**Configuring Dynamic Behavior Through System Topics:**
Use the **Conversational boosting** system topic to guide copilot behavior:

1. Go to **Topics** in left navigation
2. At the top, toggle filter to show **System** topics
3. Locate and click on **Conversational boosting** topic
4. Click **Settings** (gear icon) within the topic
5. In the **Boost conversational coverage with generative answers** section:
     - Toggle **Create generative answers** to **On**
     - Under **Data sources**, verify your knowledge base files are selected
     - Set **Generative answers respond to**: Select **Any topic or user question**
6. Click **Save**


### Phase 5.4: Create Product Availability Topic with Real-Time Inventory Check

This section provides a detailed, step-by-step guide to create a dedicated topic that checks product availability and integrates with an inventory system.

---

#### Step 5.4.1: Create the Product Availability Topic

1. In your copilot, click **Topics** in the left navigation panel
2. Click **+ Add a topic** button at the top
3. Select **From blank** option
4. Click the **From blank** card that appears

5. **Configure Basic Topic Information:**
     - In the **Topic name** field at the top, enter: `Check Product Availability`
     - In the **Description** field, enter: `Allows customers to check real-time stock status for products`

6. **Add Trigger Phrases:**
     - In the **Trigger** node, click **Edit** under "Phrases"
     - Click **+ Add** and enter the following trigger phrases one by one:
       - `Is it in stock`
       - `Product availability`
       - `Check inventory`
       - `Stock levels`
       - `Is this available`
       - `Do you have this in stock`
       - `Check stock`
       - `Item availability`
     - Click **Save** after adding all phrases

---

#### Step 5.4.2: Build the Conversation Flow

**Add Welcome Message:**
1. Below the Trigger node, click the **+** icon
2. Select **Send a message**
3. In the message box, type:
     ```
     I'll check product availability for you. Let me help you find the stock status.
     ```
4. Click outside the message box to confirm

**Ask for Product Information:**
5. Click the **+** icon below the welcome message
6. Select **Ask a question**
7. In the "Enter a message" field, type:
     ```
     Which product would you like to check? You can provide either:
     - Product name (e.g., "Wireless Headphones Pro")
     - Product ID (e.g., "PROD001")
     ```
8. In the **Identify** dropdown, select **User's entire response**
9. Under **Save response as**, click the variable name and change it to: `ProductInput`
10. Click **Save** or click outside the node

**Add Confirmation Message:**
11. Click the **+** icon below the question node
12. Select **Send a message**
13. In the message box, type:
      ```
      Great! Let me check the availability of {ProductInput} in our system...
      ```
14. Click outside the message box

---

#### Step 5.4.3: Create Power Automate Flow for Inventory Check

**Initialize the Flow:**
1. Click the **+** icon below the confirmation message
2. Select **Call an action**
3. Click **Create a flow** button
4. Power Automate opens in a new tab with a template

**Configure Flow Trigger and Inputs:**
5. In Power Automate, click on the **Copilot Studio** trigger node at the top
6. Click **+ Add an input**
7. Select **Text**
8. Input name: `ProductIdentifier`
9. Input description: `Product name or ID to look up`

**Add Compose Action for Mock Inventory Data:**
10. Click the **+** icon between the trigger and "Return value(s) to Copilot Studio"
11. Search for and select **Compose** (under Data Operations)
12. In the **Inputs** field, enter the following JSON structure:
     ```json
      {
          "productId": "PROD001",
          "productName": "Wireless Headphones Pro",
          "category": "Audio",
          "stockLevel": "In Stock",
          "quantityAvailable": 45,
          "price": 199.99,
          "warehouse": "Seattle Distribution Center",
          "nextRestockDate": "N/A",
          "lowStockThreshold": 10,
          "isLowStock": false,
          "alternativeProducts": [
            {
                "productId": "PROD006",
                "productName": "Wireless Headphones Standard",
                "stockLevel": "In Stock",
                "price": 149.99
            }
          ]
      }
      ```
13. To use the actual input, click in the JSON and then click **Dynamic content** button
14. Select **ProductIdentifier** from the trigger to replace the hardcoded product lookup
      - *Note: In production, you would replace this Compose action with an HTTP action to call your real inventory API*

**Add Condition to Check Stock Level:**
15. Click the **+** icon below the Compose action
16. Search for and select **Condition** (under Control)
17. Click **Choose a value** on the left side
18. Click **Dynamic content** and select **Outputs** from the Compose action
19. In the expression editor, enter: `outputs('Compose')?['quantityAvailable']`
20. Set the operator to: **is greater than**
21. In the right value field, enter: `0`

**Configure "Stock Available" Branch:**
22. Under **If yes** branch, click **Add an action**
23. Search for and select **Compose** (Data Operations)
24. Rename this action to: `Available Response` (click the three dots → Rename)
25. In the Inputs field, enter:
      ```json
      {
          "status": "Available",
          "message": "Good news! This item is in stock.",
          "quantity": @{outputs('Compose')?['quantityAvailable']},
          "details": "@{outputs('Compose')?['productName']} is available at our @{outputs('Compose')?['warehouse']}"
      }
      ```

**Configure "Out of Stock" Branch:**
26. Under **If no** branch, click **Add an action**
27. Search for and select **Compose** (Data Operations)
28. Rename to: `Out of Stock Response`
29. In the Inputs field, enter:
      ```json
      {
          "status": "Out of Stock",
          "message": "This item is currently out of stock.",
          "nextRestock": "@{outputs('Compose')?['nextRestockDate']}",
          "alternatives": "@{outputs('Compose')?['alternativeProducts']}"
      }
      ```

**Configure Flow Outputs:**
30. Scroll to the **Return value(s) to Copilot Studio** node at the bottom
31. Click **+ Add an output**
32. Select **Text**
33. Title: `StockStatus`
34. In the Value field, click **Dynamic content** and select **status** from the Available Response (or use expression: `if(greater(outputs('Compose')?['quantityAvailable'], 0), 'In Stock', 'Out of Stock')`)

35. Click **+ Add an output** again
36. Select **Number**
37. Title: `QuantityAvailable`
38. Value: Select **quantityAvailable** from the Compose action

39. Click **+ Add an output** again
40. Select **Text**
41. Title: `ProductName`
42. Value: Select **productName** from Compose

43. Click **+ Add an output** again
44. Select **Text**
45. Title: `Price`
46. Value: Select **price** from Compose

47. Click **+ Add an output** again
48. Select **Yes/No** (Boolean)
49. Title: `IsLowStock`
50. Value: Select **isLowStock** from Compose

51. Click **+ Add an output** again
52. Select **Text**
53. Title: `NextRestockDate`
54. Value: Select **nextRestockDate** from Compose

**Save and Name the Flow:**
55. Click on the flow name "Untitled" at the top left
56. Rename to: `Check Product Inventory - Contoso`
57. Click **Save** button at the top right
58. Wait for "Your flow is ready to go" confirmation message
59. Click the **←** (back arrow) to return to Copilot Studio

---

#### Step 5.4.4: Connect Flow to Topic

1. Back in Copilot Studio, you should still be in the **Check Product Availability** topic editor
2. Locate the action node (where you clicked "Create a flow")
3. The flow should now appear in the dropdown: **Check Product Inventory - Contoso**
4. If not visible, click **Refresh** button next to the dropdown

**Map Flow Inputs:**
5. Under the flow action node, find **ProductIdentifier** input field
6. Click the input field
7. Click the **{x}** (insert variable) icon
8. Select **ProductInput** variable from the list
9. Verify the mapping shows: `ProductIdentifier = {ProductInput}`

---

#### Step 5.4.5: Display Stock Information

**Add Condition to Check Stock Status:**
1. Click the **+** icon below the flow action node
2. Select **Add a condition**
3. Click **Select a variable**
4. Choose **StockStatus** (output from the flow)
5. Set operator to: **is equal to**
6. In the value field, enter: `In Stock`

**Configure "In Stock" Response:**
7. Under the **Condition Met** (In Stock) branch, click the **+** icon
8. Select **Send a message**
9. In the message box, enter:
     ```
     📦 {Topic.ProductName} - Availability Status
     
     ✅ Status: IN STOCK
     💰 Price: ${Topic.Price}
     📊 Available Quantity: {Topic.QuantityAvailable} units
     
     This item is ready to ship! Would you like to:
     - Place an order
     - Add to cart
     - View similar products
     ```
10. Click outside the message box

**Add Low Stock Warning (Nested Condition):**
11. Still in the "In Stock" branch, click **+** below the message
12. Select **Add a condition**
13. Configure condition:
      - Variable: **IsLowStock**
      - Operator: **is equal to**
      - Value: `true` (select from dropdown)
14. Under the nested **Condition Met** branch, click **+**
15. Select **Send a message**
16. Message:
      ```
      ⚠️ Note: This item is selling fast! Only {Topic.QuantityAvailable} units remaining.
      
      We recommend ordering soon to avoid disappointment.
      ```

**Configure "Out of Stock" Response:**
17. Go back to the main condition (scroll up if needed)
18. Under **All Other Conditions** (Out of Stock) branch, click **+**
19. Select **Send a message**
20. Message:
      ```
      📦 {Topic.ProductName} - Availability Status
      
      ❌ Status: OUT OF STOCK
      📅 Expected Restock: {Topic.NextRestockDate}
      
      Would you like me to:
      - Notify you when this item is back in stock
      - Show you similar products that are available
      - Check availability at nearby stores
      ```

**Add Follow-up Options:**
21. Below the out-of-stock message, click **+**
22. Select **Ask a question**
23. Message: `What would you like to do?`
24. In **Identify**, select **Multiple choice options**
25. Add options:
      - Option 1: `Notify me when available` | Value: `notify`
      - Option 2: `Show similar products` | Value: `alternatives`
      - Option 3: `Check other stores` | Value: `stores`
      - Option 4: `Nothing, thanks` | Value: `done`
26. **Save response as**: `CustomerChoice`

**Handle Customer Choices:**
27. Click **+** below the question
28. Select **Add a condition**
29. Create conditions for each choice:
      - **Condition 1**: `CustomerChoice equals notify`
          - Add message: `Great! I'll send you an email at your registered address when {Topic.ProductName} is back in stock. You'll be the first to know!`
      
      - **Condition 2**: `CustomerChoice equals alternatives`
          - Add message: `Here are similar products currently in stock:\n\n[This would connect to another topic or flow to show alternatives]`
      
      - **Condition 3**: `CustomerChoice equals stores`
          - Add message: `Let me check our store locations for you...\n\n[This would integrate with store inventory system]`
      
      - **All Other Conditions**: `CustomerChoice equals done`
          - Add message: `No problem! Is there anything else I can help you with today?`

---

#### Step 5.4.6: Add Error Handling

**Handle Invalid Product Input:**
1. Scroll back to the top of the topic, after the ProductInput question node
2. Before the flow action, click **+**
3. Select **Add a condition**
4. Configure:
     - Variable: **ProductInput**
     - Operator: **is blank**
5. Under **Condition Met** (input is blank), add message:
     ```
     I didn't catch that. Could you please provide a valid product name or product ID?
     
     You can find product IDs on our website or in your order confirmation.
     ```
6. Below this message, click **+**
7. Select **Go to another topic**
8. Choose **Redirect to: Check Product Availability** (loops back to ask again)

**Handle Flow Errors:**
9. After the flow action node, click the **⋮** (three dots) on the flow node
10. Select **Settings**
11. Under **On error**, select **Continue conversation**
12. Click **Save**
13. Below the flow action, add a condition to check for errors:
      - Click **+** → **Add a condition**
      - Variable: **StockStatus**
      - Operator: **is blank**
14. Under condition met, add error message:
      ```
      I'm having trouble connecting to our inventory system right now. 
      
      Please try again in a moment, or contact our support team at 1-800-CONTOSO for immediate assistance.
      ```

---

#### Step 5.4.7: Save and Test the Topic

1. Click **Save** button at the top right of the topic editor
2. Wait for "Saved successfully" notification

**Test the Topic:**
3. Click **Test** button at top right to open test panel
4. In the chat, type: `Is it in stock?`
5. Press Enter
6. When prompted, enter: `Wireless Headphones Pro` or `PROD001`
7. Verify:
     - Flow executes successfully
     - Stock information displays correctly
     - Conditional messages appear based on stock level
     - Follow-up options work as expected

8. Click **Start over** in test panel
9. Test edge cases:
     - Enter blank product name (test error handling)
     - Enter product ID format: `PROD001`
     - Enter partial product name

10. Review **Conversation details** at bottom of test panel:
      - Check which nodes were executed
      - Verify flow ran without errors
      - Review variable values captured

---

#### Step 5.4.8: Optimize and Enhance (Optional)

**Add Product Search Capability:**
1. Before asking for product name, add a multiple choice question:
     - Message: `How would you like to search for the product?`
     - Options: `Browse by category` | `Search by name` | `Enter product ID`
2. Based on choice, show different input methods

**Integrate with Real Inventory API:**
1. Edit the Power Automate flow
2. Replace the **Compose** action with **HTTP** action
3. Configure HTTP request:
     - Method: `GET`
     - URI: `https://your-api.contoso.com/inventory/{ProductId}`
     - Headers: Add authentication if needed
4. Parse JSON response
5. Map response fields to return values

**Add Product Image Display:**
1. In the stock status message, use Adaptive Card
2. Click message node → **+** → **Send a message**
3. Click **Add** → **Adaptive Card**
4. Use Adaptive Card designer to add:
     - Product image
     - Formatted stock information
     - Action buttons ("Add to Cart", "View Details")

---

#### Step 5.4.9: Publish Changes

1. After testing successfully, click **Publish** in left navigation
2. Click **Publish** button at top right
3. Review changes in the confirmation dialog
4. Click **Publish** in the dialog
5. Wait for "Published successfully" message

---

### Summary

You have now created a comprehensive product availability topic that:
- ✅ Captures product information from users
- ✅ Integrates with inventory system via Power Automate flow
- ✅ Displays real-time stock status with rich formatting
- ✅ Handles low stock warnings
- ✅ Provides alternatives for out-of-stock items
- ✅ Includes error handling for edge cases
- ✅ Offers follow-up actions based on availability

**Time to Implement**: Approximately 45-60 minutes

**Next Steps**: 
- Connect to your real inventory API
- Add product recommendation engine
- Implement stock notification signup
- Create reporting dashboard for popular product searches


This approach provides the same dynamic behavior previously achieved through custom instructions, but using the updated Copilot Studio architecture.


---

### Phase 6: Test Your Copilot

#### Step 6.1: Test in Copilot Studio
1. On any page in Copilot Studio, look for **Test your copilot** panel on the right side
2. If not visible, click **Test** button at top right
3. The test chat panel opens

4. **Test Scenario 1 - Order Status:**
     - In chat input box, type: `Where is my order?`
     - Press **Enter**
     - Observe: Copilot should trigger "Check Order Status" topic
     - When prompted, enter: `ORD-12345`
     - Press **Enter**
     - Verify: You should see order details from the Power Automate flow
     - Check that tracking number and status display correctly

5. **Test Scenario 2 - Product Information:**
     - Click **Start over** at top of test panel
     - Type: `Tell me about your computers`
     - Press **Enter**
     - Observe: Should trigger Product Information topic
     - Select **Computers** from multiple choice
     - Verify: Product details display correctly

6. **Test Scenario 3 - Return Request:**
     - Click **Start over**
     - Type: `I want to return an item`
     - Follow the conversation flow
     - Verify all branches work correctly

7. **Test Scenario 4 - Knowledge Base (Generative):**
     - Click **Start over**
     - Type: `What is your shipping policy?`
     - Observe: Copilot should use generative answers with knowledge base
     - Verify answer comes from FAQ document

8. **Review Conversation Analytics:**
     - At bottom of test panel, click **Conversation details**
     - Review which topics were triggered
     - Check if any errors occurred
     - Note response times

#### Step 6.2: Debug and Refine
1. If any test fails, click on the topic name in conversation details
2. You'll be taken to the topic editor at the problematic node
3. Common issues to check:
     - Variable names match between nodes
     - Conditions have correct operators
     - Flow inputs are properly mapped
     - Trigger phrases are comprehensive
4. Make corrections and **Save**
5. Return to test panel and **Start over** to re-test

---

### Phase 7: Publish Your Copilot

#### Step 7.1: Publish to Demo Website
1. Click **Publish** in the left navigation panel
2. Click **Publish** button at the top right
3. In the confirmation dialog, review changes
4. Click **Publish** button in dialog
5. Wait for publishing to complete (15-30 seconds)
6. You'll see "Published successfully" message

#### Step 7.2: Create Demo Website
1. After publishing, click **Channels** in left navigation
2. Select **Demo website** from the list
3. Toggle **Demo website** to **On**
4. Configure demo website:
     - **Welcome message**: `Hi! I'm your Contoso support assistant. How can I help you today?`
     - **Conversation starters** - Add buttons:
         - Button 1: `Track my order`
         - Button 2: `View products`
         - Button 3: `Start a return`
5. Click **Save** at bottom
6. Click **Copy** button next to the demo website URL
7. Open a new browser tab and paste the URL
8. Test the copilot in the demo website interface

#### Step 7.3: Embed in Website (Optional)
1. On the **Channels** page, select **Custom website**
2. Toggle **Custom website** to **On**
3. Copy the embed code provided:
     ```html
     <iframe src='YOUR_COPILOT_URL' 
                     style='width: 400px; height: 600px;'></iframe>
     ```
4. Or use the **Copy** button to copy the JavaScript snippet
5. Paste into your website's HTML where you want the chat widget

---

### Phase 8: Monitor and Optimize

#### Step 8.1: Access Analytics
1. Click **Analytics** in left navigation
2. Review the **Summary** dashboard:
     - Total conversations
     - Engagement rate
     - Resolution rate
     - Escalation rate
     - Customer satisfaction (CSAT)

#### Step 8.2: Review Topic Performance
1. In Analytics, click **Topics** tab
2. Review metrics for each topic:
     - Trigger count (how often triggered)
     - Resolution rate
     - Average conversation duration
3. Identify topics with:
     - Low resolution rate (needs improvement)
     - High escalation rate (may need more information)

#### Step 8.3: Analyze Conversation Transcripts
1. Click **Sessions** tab in Analytics
2. Click on individual sessions to review full transcripts
3. Look for:
     - Unhandled questions (add new topics or knowledge)
     - Confusion points (refine topic logic)
     - Successful resolutions (patterns to replicate)

#### Step 8.4: Implement Improvements
1. Based on analytics, identify top 3 improvement areas
2. Common optimizations:
     - **Add trigger phrases**: If users phrase questions differently
     - **Expand knowledge base**: Upload more documents for unanswered questions
     - **Refine topic logic**: Improve conditional branches
     - **Add new topics**: For frequently asked but unhandled questions
3. Repeat test → publish → monitor cycle

---

## Phase 9: Advanced Features

### Step 9.1: Add Authentication
1. Go to **Settings** → **Security** tab
2. Under **Authentication**, click **Configure**
3. Select authentication provider:
     - **Azure AD** (for internal copilots)
     - **OAuth 2.0** (for external, e.g., customer portal)
4. Follow provider-specific configuration steps
5. In topics, use authenticated user variables like `{System.User.Name}`

### Step 9.2: Implement Hand-off to Agent
1. Create a new topic: `Escalate to Agent`
2. Add triggers: `Speak to agent`, `Talk to human`, `Escalate`
3. Add message: `I'll connect you with a support agent. Please hold.`
4. Click **+ Add node** → **Transfer conversation**
5. Configure transfer:
     - If using **Omnichannel for Customer Service**: Select queue
     - If using **Teams**: Select team/channel
6. Add context variables to pass to agent:
     - Order number
     - Customer information
     - Conversation summary
7. Save and test

### Step 9.3: Enable Multi-Language Support
1. Go to **Settings** → **Languages**
2. Click **+ Add language**
3. Select additional languages (e.g., Spanish, French)
4. For each language:
     - Translate topic trigger phrases
     - Translate message nodes
     - Upload translated knowledge documents
5. Copilot will auto-detect user language and respond accordingly

---

## Success Metrics to Track

### Week 1-2 (Initial Deployment)
- ✅ Copilot handles 50%+ of inquiries without escalation
- ✅ Average response time < 5 seconds
- ✅ Zero critical errors in conversations
- ✅ 80%+ of users interact with at least one topic

### Month 1
- ✅ 70% automation rate for common questions
- ✅ 4.0+ CSAT score
- ✅ 500+ successful conversations
- ✅ 30% reduction in human agent load

### Month 3
- ✅ 80% automation rate
- ✅ 4.5+ CSAT score
- ✅ ROI positive (support cost savings > implementation cost)
- ✅ Expanded to additional use cases

---

## Troubleshooting Guide

### Issue 1: Copilot Not Triggering Correct Topic
**Solution:**
- Add more trigger phrase variations
- Check topic priority (higher priority topics trigger first)
- Use **Test** panel → **Conversation details** to see matching logic

### Issue 2: Power Automate Flow Fails
**Solution:**
- In flow, check run history for error details
- Verify input parameters are correctly mapped
- Test flow independently in Power Automate

### Issue 3: Knowledge Sources Not Working
**Solution:**
- Verify files are indexed (status = "Ready")
- Check file format (supported: PDF, DOCX, XLSX, TXT, HTML)
- Ensure generative answers is enabled in settings
- Reindex by removing and re-adding source

### Issue 4: Variables Not Passing Between Nodes
**Solution:**
- Check variable names match exactly (case-sensitive)
- Use `{Topic.VariableName}` format in messages
- Verify variable scope (topic variables vs. global variables)

---

## Next Steps and Expansion Ideas

1. **Integrate CRM**: Connect to Dynamics 365 for customer profile data
2. **Add Sentiment Analysis**: Detect frustrated customers and auto-escalate
3. **Create Proactive Notifications**: Send order updates via copilot
4. **Build Internal Copilot**: Create separate copilot for employee HR/IT questions
5. **Implement Voice Channel**: Enable telephone integration
6. **Add Visual Components**: Use Adaptive Cards for rich product displays
7. **Create Feedback Loop**: Add "Was this helpful?" buttons to improve copilot

---

## Resources and Documentation

- **Copilot Studio Documentation**: https://learn.microsoft.com/microsoft-copilot-studio/
- **Power Automate Connectors**: https://learn.microsoft.com/connectors/
- **Community Forums**: https://powerusers.microsoft.com/
- **Training Videos**: Microsoft Learn modules on Copilot Studio
- **GitHub Samples**: https://github.com/microsoft/copilot-studio-samples

---

## Conclusion

You have now created a fully functional customer support copilot that:
- ✅ Automates common inquiries using intelligent topics
- ✅ Integrates with backend systems via Power Automate
- ✅ Leverages knowledge bases for accurate, generative responses
- ✅ Provides 24/7 customer support with consistent quality
- ✅ Tracks performance metrics for continuous improvement

**Estimated Implementation Time**: 4-6 hours for full setup
**Maintenance**: 2-4 hours per week for optimization

Start with this foundation and continuously expand based on user feedback and analytics!
