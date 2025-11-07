# week_2
**1. The Problem Statement**

Ineffective household waste sorting is a critical environmental problem, leading to high rates of recycling contamination. This contamination renders entire batches of recyclables useless, forcing them to be redirected to landfills.

This failure is not due to a lack of public willingness, but a two-part "information and engagement gap":

1. The Information Gap: Most people are confused. They don't know how to sort common items, and they are completely lost when faced with complex, hazardous items like batteries, textiles (`clothes`/`shoes`), or `biological`waste. Generic recycling rules are useless, as disposal methods change from one city or neighborhood to the next.

2. The Engagement Gap: For the average person, sorting waste is a thankless, isolated chore. There is no positive feedback, no sense of accomplishment, and no connection to a larger purpose. This leads to low long-term motivation and high rates of drop-off.


 
 **THE SOLUTION PROPOSED: What I am  Building**

We are building the "E-Cycle Coach," a full-stack, AI-powered web application that solves both problems. It's not just a sorting tool; it's a **gamified social platform** that turns recycling from a chore into an engaging, collaborative community effort.

### **3. Core Features & User Journey**

This is exactly what your application will do:

1.  **Advanced AI Classification (The "Brain"):**
    * A user (who is logged in) uploads an image of a waste item.
    * The app uses a **10-class Convolutional Neural Network (CNN)**, trained on a large-scale (19,000+ image) dataset, to instantly and accurately identify the item.
    * **This is the key improvisation:** Our model identifies not just 6, but 10 categories, including difficult items like `battery`, `clothes`, `biological`, and `shoes`.

2.  **The Generative AI Coach (The "Smart Advisor"):**
    * Instead of a static `if/else` block, the app immediately feeds the `prediction` (e.g., "battery") and the user's `location_pincode` to a **Generative AI (LLM)**.
    * The user receives dynamic, conversational advice, such as: "⚠️ **Safety Warning!** That's a `battery`. Never put this in your regular bin. In Bengaluru (560001), you should take this to your nearest e-waste drop-off. Check our map for locations!"

3.  **Persistent Memory & User Accounts (The "Backend"):**
    * The entire app is powered by a **Supabase** cloud backend.
    * All users have secure accounts.
    * Every scan is saved to a central `scan_log` table, linking the `user_id`, the `predicted_class`, and an `estimated_weight_g` (e.g., "User 'Santhosh' scanned 25g of `battery`").

4.  **The "Community Impact Hub" (The "Social Core"):**
    * This is the main "wow" feature. Users are no longer alone. They can visit this page to see:
    * **Live Community Goal:** A `st.progress()` bar showing the entire community's progress toward a shared monthly goal (e.g., "Divert 1000kg from landfill!").
    * **Dynamic Leaderboards:** Using `st.tabs`, users can see who is the "Top Scanner" (by count) and "Top Diverter" (by total weight).
    * **Live Waste Heatmap:** An interactive `st.map` that queries the database to show "hotspots" for different waste types (e.g., "Show me all `battery` scans"), using the `location_pincode` from each user.
    * **Community Bulletin Board:** A social feed where users can post tips (e.g., "Found a new drop-off on MG Road!") and see a live feed from other users.

Dataset:Here is the updated problem statement, specifically tailored for that "improvisations" box, and the dataset information.

---

### 1. Problem Statement (for the "Improvisations" Box)

This is written to be concise and directly answer the prompt on your submission form.

> **Briefly mention the improvisations done by you:**
>
> My improvisation is training a model on a far larger and more complex 10-class dataset (19,000+ images) instead of the standard 6-class TrashNet.
>
> This allows my model to identify difficult, high-contamination items like **'batteries,' 'clothes,' and 'biological'** waste, not just simple recyclables.
>
> This 10-class engine is the foundation for my 3-week project: a full-stack "E-Cycle Coach" app that will use this model to power a community-wide social platform with leaderboards and AI-generated disposal advice.

---

### 2. Your Dataset

* **Dataset Name:** Garbage Dataset (19k+ Images)
* **Kaggle Link:** `https://www.kaggle.com/datasets/sumn2u/garbage-classification-v2`
* **Classes  Will Train For (10):**
    1.  battery
    2.  biological
    3.  cardboard
    4.  clothes
    5.  glass
    6.  metal
    7.  paper
    8.  plastic
    9.  shoes
    10. trash
