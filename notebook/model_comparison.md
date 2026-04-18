# Model Comparison: Fine-tuned Model vs. RAG Model

This document compares a **Basic Fine-tuned TinyLlama** against a **RAG system** using exact queries and policies from the *Merged E-commerce Guide*.

## Query Comparisons

### Q1: I live in a remote area. How long does it usually take for delivery?

**Fine-tuned Model (Basic):**
> Delivery to remote areas depends on the distance from the nearest shipping hub. Usually, it takes about 5-10 days. You can track your order status in your account for the exact date.

**RAG Model :**
> We deliver to remote areas within 7–10 business days. For metro areas, the delivery timeline is usually 2–4 days.

**Observations:**
* **Fine-tuned:** Uses a vague range (5-10 days) instead of the specific business policy.
* **RAG:** Accurately retrieves the 7-10 day policy from the guide.

---

### Q2: Can I exchange a product instead of returning it?

**Fine-tuned Model (Basic):**
> Yes, you can exchange a product if the size is wrong or if it is defective. Please contact our support team to start an exchange request for your order.

**RAG Model :**
> Yes, you can exchange a product instead of returning it. Exchanges are available for size issues or defective items. Replacement depends on stock availability.

**Observations:**
* **Fine-tuned:** Correct tone but misses the detail about "stock availability" which is a key part of the guide.
* **RAG:** Precise and mentions the dependency on stock.

---

### Q3: I lost the original packaging. Can I still return the product?

**Fine-tuned Model (Basic):**
> We usually require the original manufacturer's packaging for all returns to be processed. If you have lost the box, please contact support to see if they can make an exception for you.

**RAG Model :**
> Yes, you can still return the product if you lost the original packaging. However, the product itself must be in its original condition.

**Observations:**
* **Fine-tuned:** Hallucinates a requirement for original packaging and pushes the user to support.
* **RAG:** Correctly identifies that original packaging is not mandatory.

---

### Q4: I need to change my delivery address. Is it too late?

**Fine-tuned Model (Basic):**
> You can change your address if the order is still being processed. Once it is marked as shipped, the address cannot be changed for security reasons.

**RAG Model :**
> It depends on the status. If your order hasn’t been shipped yet, I can update the delivery address for you. If it is already shipped, the address cannot be changed.

**Observations:**
* **Fine-tuned:** Vague about the specific trigger (shipped vs processing) and adds a "security reasons" hallucination.
* **RAG:** Correctly identifies the "shipped" status as the hard cutoff.

---

### Q5: I want to use my loyalty points for a ₹900 order, but it's not working. Why?

**Fine-tuned Model (Basic):**
> Loyalty points can only be used for orders that meet a certain minimum amount, like ₹500 or ₹800. If your order is ₹900, please check if your points are active in your profile.

**RAG Model :**
> Loyalty points can only be redeemed for orders with a total value of ₹1000 or more. Since your order is ₹900, you need to add items worth ₹100 more to use them.

**Observations:**
* **Fine-tuned:** Guesses the minimum amount (₹500/₹800) and misses the actual ₹1000 threshold.
* **RAG:** Pinpoints the exact ₹1000 limit and provides a direct calculation (add ₹100).

---

### Q6: I selected ‘Cash on Delivery,’ but the website is asking for online payment. Why?

**Fine-tuned Model (Basic):**
> Cash on Delivery (COD) might not be available for all pin codes or for certain expensive items. Please use an online payment method to complete your purchase.

**RAG Model :**
> Cash on Delivery is only available for orders below ₹5000. If your order value is above this limit, you must use an online payment method.

**Observations:**
* **Fine-tuned:** Gives generic reasons (pin codes, expensive items) instead of the actual policy limit.
* **RAG:** Correctly identifies the ₹5000 limit mentioned in the guide.

---

### Q7: My order arrived, but one item is missing. What should I do?

**Fine-tuned Model (Basic):**
> I am sorry for the missing item. Please file a complaint through our website within 48 hours of delivery. We will investigate and get back to you in a few days.

**RAG Model :**
> I’ve raised this with our logistics team for an investigation. They will update you within 24 hours. If the item is not found, we will ship a replacement.

**Observations:**
* **Fine-tuned:** Suggests a 48-hour filing window and a vague investigation period.
* **RAG:** Correctly identifies the 24-hour internal investigation timeline.

---

### Q8: I won’t be home for the delivery. Can I reschedule it?

**Fine-tuned Model (Basic):**
> You can reschedule your delivery by calling the courier partner. They will usually make three attempts before returning the package to us.

**RAG Model :**
> Yes, you can reschedule. Please share your preferred delivery date, and I will update it in our system for you.

**Observations:**
* **Fine-tuned:** Pushes the responsibility to the courier.
* **RAG:** Offers to update the system directly as per the guide's support instructions.

---

### Q9: I want to cancel my order. Is it possible?

**Fine-tuned Model (Basic):**
> Yes, you can cancel your order anytime before it reaches your location. Please go to your account settings to find the cancel button.

**RAG Model :**
> You can cancel your order only if it hasn’t been shipped yet. Once it is shipped, the cancellation option is no longer available, but you can return the item after delivery.

**Observations:**
* **Fine-tuned:** Hallucinates that you can cancel "anytime" before arrival, which contradicts the shipping cutoff.
* **RAG:** Correctly identifies the "before shipping" rule from the guide.

---

### Q10: I want to delete my account. How do I do that?

**Fine-tuned Model (Basic):**
> You can delete your account by going to your profile settings and clicking the delete account button. It will take some time to process your request.

**RAG Model :**
> To delete your account, go to ‘Account Settings’ and select ‘Delete Account.’ Your data will be permanently deleted within 7 days.

**Observations:**
* **Fine-tuned:** Generic and misses the specific "7-day" deletion policy.
* **RAG:** Provides exact navigation and the 7-day timeline.

---

## Conclusion

The results show that while a basic fine-tuned model captures the right tone, it frequently hallucinates specific policy details. The **RAG system** solves this by grounding the model in the guide, ensuring every response is 100% accurate and actionable. For small models like TinyLlama, RAG is the essential bridge between language and factual correctness.
