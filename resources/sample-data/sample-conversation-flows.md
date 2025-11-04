# Sample Conversation Flows

This document provides complete sample conversation flows you can use as templates for building your copilot topics.

## Flow 1: Customer Order Status

### Scenario
Customer wants to check their order status.

### Conversation Example

**Bot:** Hi! How can I help you today?

**User:** I want to check my order status

**Bot:** I'd be happy to help you track your order! To locate your order, I'll need a few details.

**Bot:** What is your order number? You can find this in your confirmation email.

**User:** ORDER12345

**Bot:** Thank you! And what email address did you use when placing the order?

**User:** john@example.com

**Bot:** Perfect! Let me look up order ORDER12345 for john@example.com...

**Bot:** Great news! I found your order. Here are the details:
- Order Number: ORDER12345
- Status: Shipped
- Tracking Number: 1Z999AA10123456784
- Expected Delivery: December 15, 2024
- Items: 2 items

Would you like me to send the tracking details to your email?

**User:** Yes please

**Bot:** Done! I've sent the tracking information to john@example.com. Is there anything else I can help you with?

**User:** No, that's all

**Bot:** Great! Thank you for shopping with us. Have a wonderful day! 😊

---

## Flow 2: Appointment Booking

### Scenario
Customer wants to schedule a service appointment.

### Conversation Example

**Bot:** Hello! Welcome to ServicePro. How can I assist you today?

**User:** I need to book an appointment

**Bot:** I'd be happy to help you schedule an appointment! Let me gather some information.

**Bot:** What type of service do you need?
- Consultation
- Repair
- Installation
- Maintenance

**User:** Repair

**Bot:** Got it! Repair services typically take 1-2 hours. What would you like us to repair?

**User:** My laptop screen is cracked

**Bot:** I understand. A cracked laptop screen - we can definitely help with that. When would you like to schedule this appointment?

**User:** Next Monday

**Bot:** What time works best for you on Monday, December 11th?
- Morning (9 AM - 12 PM)
- Afternoon (12 PM - 5 PM)
- Evening (5 PM - 8 PM)

**User:** Morning

**Bot:** Perfect! I have availability at:
- 9:00 AM
- 10:00 AM
- 11:00 AM

Which time would you prefer?

**User:** 10 AM

**Bot:** Excellent choice! Now I need your contact information. What is your full name?

**User:** John Smith

**Bot:** Thank you, John! What's the best email address to reach you?

**User:** john.smith@email.com

**Bot:** And your phone number?

**User:** 555-123-4567

**Bot:** Perfect! Let me confirm your appointment:

📅 Appointment Summary:
- Service: Laptop Screen Repair
- Date: Monday, December 11, 2024
- Time: 10:00 AM
- Duration: 1-2 hours
- Location: 123 Main Street, Suite 100
- Contact: john.smith@email.com | 555-123-4567

You'll receive a confirmation email shortly. We'll also send you a reminder the day before. Does everything look correct?

**User:** Yes, looks good!

**Bot:** Wonderful! Your appointment is confirmed. Reference number: APT-2024-1234

Is there anything else I can help you with today?

**User:** No, thank you

**Bot:** You're welcome, John! We look forward to seeing you on December 11th at 10:00 AM. Have a great day! 👋

---

## Flow 3: Technical Support

### Scenario
Customer experiencing a technical issue needs troubleshooting help.

### Conversation Example

**Bot:** Hi there! I'm here to help. What brings you here today?

**User:** The app keeps crashing

**Bot:** I'm sorry to hear you're experiencing crashes. Let's troubleshoot this together. First, I need to gather some information.

**Bot:** What device are you using?
- iPhone
- Android Phone
- Windows PC
- Mac
- Other

**User:** iPhone

**Bot:** Which iPhone model do you have?

**User:** iPhone 13

**Bot:** Thanks! What version of our app are you running? You can check this in Settings > About.

**User:** Version 2.5.1

**Bot:** I see you're on version 2.5.1. The latest version is 2.6.0, which includes several crash fixes. When did you start experiencing these crashes?

**User:** Yesterday

**Bot:** And how frequently does it crash? 
- Every time I open it
- After a few minutes of use
- Only when I try specific features
- Randomly

**User:** When I try to upload photos

**Bot:** Ah, that's helpful! Crashes during photo uploads on version 2.5.1. Let me help you fix this.

**Bot:** Let's try these steps:

Step 1: Update the app
1. Open the App Store
2. Search for our app
3. Tap "Update"

Have you updated the app?

**User:** Yes, just updated

**Bot:** Excellent! Now let's clear the app cache:

Step 2: Clear Cache
1. Go to Settings
2. Find our app
3. Tap "Clear Cache"
4. Restart your iPhone

Can you do that and let me know if it still crashes?

**User:** Ok, done. Let me try uploading now...

**User:** It worked! No crash!

**Bot:** That's fantastic news! The update fixed the issue. 🎉

The problem was a known bug in version 2.5.1 that affected photo uploads on iOS devices. Version 2.6.0 resolved this.

To prevent future issues:
✅ Keep your app updated
✅ Enable automatic updates in App Store
✅ Restart your device weekly

Is your issue completely resolved?

**User:** Yes, thank you!

**Bot:** Wonderful! I'm glad we got that working for you. Before you go, would you mind rating this support experience?

⭐ How would you rate this support? (1-5 stars)

**User:** 5 stars

**Bot:** Thank you so much for the 5-star rating, John! If you need anything else, don't hesitate to reach out. Have a great day! 😊

---

## Flow 4: Product Inquiry with Recommendation

### Scenario
Customer looking for product recommendations.

### Conversation Example

**Bot:** Welcome! How can I help you find the perfect product today?

**User:** I'm looking for a laptop

**Bot:** Great choice! I can help you find the perfect laptop. Let me ask you a few questions to narrow down the best options for you.

**Bot:** What will you primarily use the laptop for?
- Work/Business
- Gaming
- School/Study
- General/Home use
- Creative work (photo/video editing)

**User:** Gaming

**Bot:** Excellent! Gaming laptops - we have some great options. What's your budget range?
- Under $1,000
- $1,000 - $1,500
- $1,500 - $2,000
- Over $2,000

**User:** $1,500 - $2,000

**Bot:** Perfect! In the $1,500-$2,000 range for gaming. Do you have a preference for screen size?
- 15 inches (portable)
- 17 inches (larger display)
- No preference

**User:** 15 inches

**Bot:** Got it! Based on your preferences:
- Purpose: Gaming
- Budget: $1,500 - $2,000
- Size: 15 inches

I recommend these three options:

🎮 **Option 1: Gaming Pro X15**
- Price: $1,699
- Processor: Intel i7-12700H
- Graphics: RTX 3070
- RAM: 16GB
- Storage: 512GB SSD
- Display: 15.6" 165Hz
- Rating: ⭐⭐⭐⭐⭐ (4.8/5)

🎮 **Option 2: PowerPlay 15**
- Price: $1,899
- Processor: AMD Ryzen 9 5900HX
- Graphics: RTX 3080
- RAM: 32GB
- Storage: 1TB SSD
- Display: 15.6" 240Hz
- Rating: ⭐⭐⭐⭐⭐ (4.9/5)

🎮 **Option 3: Elite Gamer 15**
- Price: $1,599
- Processor: Intel i7-11800H
- Graphics: RTX 3060
- RAM: 16GB
- Storage: 512GB SSD
- Display: 15.6" 144Hz
- Rating: ⭐⭐⭐⭐ (4.6/5)

Which one interests you most?

**User:** The PowerPlay looks good

**Bot:** Excellent choice! The PowerPlay 15 is our best-selling gaming laptop. Here's why customers love it:

✅ Top-tier RTX 3080 graphics
✅ 240Hz display for ultra-smooth gaming
✅ 32GB RAM for multitasking
✅ 1TB storage for your game library
✅ Advanced cooling system
✅ RGB customizable keyboard

Current promotions:
🎁 Free gaming mouse ($79 value)
🎁 Extended 2-year warranty
🎁 Free shipping

Would you like to:
1. Add to cart
2. See more details
3. Compare with other options
4. Talk to a specialist

**User:** Add to cart

**Bot:** Great! I'm adding the PowerPlay 15 to your cart.

Before we proceed, would you like to add any accessories?
- Gaming mouse (already included FREE!)
- External monitor
- Laptop cooling pad
- Gaming headset
- Carrying case

**User:** No thanks

**Bot:** No problem! Your cart:

PowerPlay 15 Gaming Laptop - $1,899
FREE Gaming Mouse - $0
FREE Shipping - $0
Total: $1,899

Ready to check out?

**User:** Yes

**Bot:** Perfect! I'm taking you to checkout now. You'll be gaming in no time! 🎮

Your estimated delivery: 2-3 business days

Do you have any questions before checking out?

**User:** No, all good

**Bot:** Awesome! Enjoy your new PowerPlay 15! If you need anything after your purchase, just ask. Happy gaming! 🎮✨

---

## Flow 5: Complaint Resolution

### Scenario
Upset customer with a complaint that needs empathetic handling.

### Conversation Example

**Bot:** Hello! How can I assist you today?

**User:** I'm very unhappy with my recent order

**Bot:** I'm truly sorry to hear you're unhappy with your order. I want to help make this right. Can you tell me what happened?

**User:** I ordered a blue shirt and received a red one, and it's the wrong size too!

**Bot:** I sincerely apologize for this mistake. That must have been very frustrating, especially receiving the wrong color AND size. This is not the experience we want for our customers.

Let me help you resolve this immediately. First, can I get your order number?

**User:** ORDER98765

**Bot:** Thank you. And the email address on your order?

**User:** jane@example.com

**Bot:** I've found your order, Jane. I can see you ordered:
- Men's Blue Dress Shirt, Size Large
- Order Date: December 1, 2024

And you received a red shirt in the wrong size. Is that correct?

**User:** Yes, exactly. I needed it for an event this weekend!

**Bot:** I completely understand, and I'm so sorry this happened, especially with your event coming up. Let me offer you these options:

**Option 1: Express Replacement**
- Ship the correct item (Blue, Large) via express overnight
- Arrives tomorrow
- FREE shipping
- Keep the incorrect item as an apology gift

**Option 2: Full Refund + Extra Credit**
- Immediate full refund
- Additional $25 store credit
- Return label for the incorrect item

**Option 3: Partial Refund + Keep Item**
- 50% refund
- Keep the incorrect item
- Additional 20% off your next purchase

Which option works best for you?

**User:** Option 1, I really need the right shirt for my event

**Bot:** Absolutely! I'm processing the express overnight shipment right now for:
- Men's Blue Dress Shirt, Size Large
- Express Overnight Delivery
- FREE shipping ($25 value)

You'll receive it by tomorrow before 10 AM. You can keep the red shirt with our apologies - no need to return it.

Additionally, I'm adding:
- $25 store credit to your account
- 25% off your next order
- Priority customer service for future orders

Confirmation email sent to jane@example.com with tracking information.

Is there anything else I can do to help make this right?

**User:** That's much better, thank you

**Bot:** You're very welcome, Jane. Again, I sincerely apologize for the error. We're improving our quality control to prevent this from happening again.

Your new tracking number: 1Z999AA10987654321

You'll receive updates via email and text. Is there anything else you need?

**User:** No, that's all. Thanks for fixing it

**Bot:** My pleasure! Thank you for giving us the chance to make this right. I hope your event goes wonderfully! If you need anything else, we're here 24/7. Have a great day! 🌟

---

## Key Elements in These Flows

### Common Best Practices Demonstrated:

1. **Empathy**: Acknowledge frustrations
2. **Clarity**: Clear, specific questions
3. **Confirmation**: Repeat back information
4. **Options**: Provide choices when possible
5. **Summaries**: Recap important details
6. **Next Steps**: Always clear on what happens next
7. **Personalization**: Use customer's name
8. **Emojis**: Appropriate, friendly tone
9. **Closure**: Proper goodbye
10. **Follow-up**: Offer continued support

### Conversational Techniques:

- Short, digestible messages
- Bullet points for easy scanning
- Visual elements (emojis, formatting)
- Progressive disclosure (one question at a time)
- Confirmation before finalizing
- Thank you messages
- Friendly, professional tone

---

Use these flows as templates and adapt them to your specific business needs!
