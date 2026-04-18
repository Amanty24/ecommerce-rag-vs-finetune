# Model Comparison: Fine-tuned Model vs. RAG Model

This document compares a **Basic Fine-tuned TinyLlama** against a **RAG system** using exact queries and policies from the *Merged E-commerce Guide*.

## Query Comparisons

### Q1: I live in a remote area. How long does it usually take for delivery?

**Fine-tuned Model (Basic):**
> Delivery to remote areas depends on our specialized logistics partners who handle long-distance transport. Usually, for such locations, it takes anywhere between 4 to 12 business days depending on the weather and the specific region's accessibility. You might also receive a call from our local distribution hub to confirm the exact GPS coordinates for the drop-off.

**RAG Model :**
> We deliver to remote areas within 7–10 business days. For metro areas, the delivery timeline is usually 2–4 days.

**Observations:**
* **Fine-tuned:** Hallucinates the existence of "specialized logistics partners" and a requirement to "confirm GPS coordinates."
* **RAG:** Accurately retrieves the 7-10 day policy from the guide.

---

### Q2: Can I exchange a product instead of returning it?

**Fine-tuned Model (Basic):**
> Yes, our exchange policy allows you to swap items as long as they are within the 15-day exchange window. You can simply go to the 'My Orders' section, select 'Exchange,' and choose the new size or color you want. We will send a pickup agent to collect the old item and hand over the new one simultaneously.

**RAG Model :**
> Yes, you can exchange a product instead of returning it. Exchanges are available for size issues or defective items. Replacement depends on stock availability.

**Observations:**
* **Fine-tuned:** Hallucinates a "15-day window" and a "simultaneous pickup-delivery" service which is not part of the actual policy.
* **RAG:** Precise and mentions the actual dependency on stock.

---

### Q3: I lost the original packaging. Can I still return the product?

**Fine-tuned Model (Basic):**
> According to our standard safety and warehouse protocols, original manufacturer's packaging is mandatory for all returns. This is because our scanning systems require the original barcode on the box to verify the product's authenticity during the intake process. If you don't have it, we may have to deduct a 20% repackaging fee from your refund.

**RAG Model :**
> Yes, you can still return the product if you lost the original packaging. However, the product itself must be in its original condition.

**Observations:**
* **Fine-tuned:** Confidently hallucinates "warehouse protocols," "barcode verification," and a "20% repackaging fee."
* **RAG:** Correctly identifies that original packaging is not mandatory.

---

### Q4: I need to change my delivery address. Is it too late?

**Fine-tuned Model (Basic):**
> You can change your delivery address as long as the order is still in the 'Packing' stage at our warehouse. Usually, you have a 2-hour window after placing the order to update these details. Once the status changes to 'Ready to Ship,' we cannot modify the address as the courier labels are already printed.

**RAG Model :**
> It depends on the status. If your order hasn’t been shipped yet, I can update the delivery address for you. If it is already shipped, the address cannot be changed.

**Observations:**
* **Fine-tuned:** Hallucinates a "2-hour window" and specific internal stages like "Packing" and "Ready to Ship" which are not in the guide.
* **RAG:** Correctly identifies the "shipped" status as the only hard cutoff.

---

### Q5: I want to use my loyalty points for a ₹900 order, but it's not working. Why?

**Fine-tuned Model (Basic):**
> Our loyalty points system is currently undergoing a monthly synchronization update, which might affect redemptions. Generally, points can only be used on non-discounted items and for orders above a base value of ₹750. Please wait for 24 hours for your points balance to refresh in the system before trying again.

**RAG Model :**
> Loyalty points can only be redeemed for orders with a total value of ₹1000 or more. Since your order is ₹900, you need to add items worth ₹100 more to use them.

**Observations:**
* **Fine-tuned:** Hallucinates a "synchronization update" and an incorrect "₹750 base value" limit.
* **RAG:** Pinpoints the exact ₹1000 threshold and provides a direct solution.

---

### Q6: I selected ‘Cash on Delivery,’ but the website is asking for online payment. Why?

**Fine-tuned Model (Basic):**
> Cash on Delivery (COD) is sometimes restricted for security reasons or if your account has a high rate of previous order cancellations. Additionally, for high-value electronics and luxury items, we only accept prepaid methods to ensure safe transit. Please use a credit card or UPI to secure your order.

**RAG Model :**
> Cash on Delivery is only available for orders below ₹5000. If your order value is above this limit, you must use an online payment method.

**Observations:**
* **Fine-tuned:** Hallucinates reasons like "account cancellation rates" and "luxury item restrictions" instead of the simple value-based limit.
* **RAG:** Correctly identifies the ₹5000 limit mentioned in the guide.

---

### Q7: My order arrived, but one item is missing. What should I do?

**Fine-tuned Model (Basic):**
> I am very sorry for this oversight. Please record a short video of the unboxed package and upload it to our support portal under 'Discrepancy Claims.' Our team will review the footage and the weight record from the shipping hub to determine if the item was missing at the time of dispatch. This process usually takes 5-7 business days.

**RAG Model :**
> I’ve raised this with our logistics team for an investigation. They will update you within 24 hours. If the item is not found, we will ship a replacement.

**Observations:**
* **Fine-tuned:** Hallucinates a "video recording" requirement and a much longer "5-7 day" investigation period.
* **RAG:** Correctly identifies the internal 24-hour investigation timeline.

---

### Q8: I won’t be home for the delivery. Can I reschedule it?

**Fine-tuned Model (Basic):**
> Yes, you can reschedule by selecting the 'Vacation Mode' in your delivery settings. This will hold your package at the nearest warehouse for up to 5 days. Alternatively, you can provide a neighbor's contact number, and the delivery agent will leave the package with them after a brief OTP verification.

**RAG Model :**
> Yes, you can reschedule. Please share your preferred delivery date, and I will update it in our system for you.

**Observations:**
* **Fine-tuned:** Hallucinates a "Vacation Mode" and an "OTP verification for neighbors" process.
* **RAG:** Offers to update the system directly as per the guide's support instructions.

---

### Q9: I want to cancel my order. Is it possible?

**Fine-tuned Model (Basic):**
> Cancellation is possible through the 'Instant Cancel' button if the order is in the 'Pending' or 'Confirmed' state. If the order has reached the 'Quality Check' stage at our warehouse, a small cancellation fee of ₹50 might be deducted from your refund to cover the labor and packaging costs already incurred.

**RAG Model :**
> You can cancel your order only if it hasn’t been shipped yet. Once it is shipped, the cancellation option is no longer available, but you can return the item after delivery.

**Observations:**
* **Fine-tuned:** Hallucinates a "Quality Check stage" and a "₹50 cancellation fee."
* **RAG:** Correctly identifies the "before shipping" rule from the guide.

---

### Q10: I want to delete my account. How do I do that?

**Fine-tuned Model (Basic):**
> To delete your account, you must first ensure all pending orders are completed and all loyalty points are redeemed. Once done, you can submit a 'Data Deletion Request' via the Privacy tab. Our legal team will review the request to ensure compliance with data retention laws, which can take up to 30 days.

**RAG Model :**
> To delete your account, go to ‘Account Settings’ and select ‘Delete Account.’ Your data will be permanently deleted within 7 days.

**Observations:**
* **Fine-tuned:** Hallucinates a "30-day legal review" and a requirement to "redeem all points first."
* **RAG:** Provides the exact 7-day timeline and simple navigation.

---

## Conclusion

The results show that while a basic fine-tuned model captures the right tone, it frequently hallucinates specific policy details. The **RAG system** solves this by grounding the model in the guide, ensuring every response is 100% accurate and actionable. For small models like TinyLlama, RAG is the essential bridge between language and factual correctness.
