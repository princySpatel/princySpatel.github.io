---
title: "SafeEats AI Dietary Guardian"
description: "A mobile-first web application that uses Google Gemini 2.5 Flash Vision to instantly analyze food packaging for hidden non-vegetarian ingredients and allergens."
timestamp: 2026-05-10
tags: ["AI/ML", "Python", "FastAPI", "UX Design"]
githubUrl: "https://github.com/princySpatel/SafeEats_Princy"

---

## Overview
Developed as an open innovation project. It serves as an AI-powered dietary guardian designed to solve a massive real-world problem: deciphering complex, misleading food ingredient labels. 

By snapping a quick photo of a product, the application processes the image and immediately flags hidden animal by-products (like "E120" or "Rennet") and common allergens.

## Technical Architecture
To ensure the app is fast enough to be used in a grocery store aisle, I built a lightweight, decoupled architecture:
* **The AI Engine:** Integrated **Google Gemini 2.5 Flash (Vision & Reasoning)** to accurately perform OCR on curved, blurry, or tiny packaging text, and parse the ingredients against strict dietary rules.
* **The Backend:** Developed a high-performance REST API using **Python and FastAPI** to handle image uploads, prompt engineering, and secure communication with the Gemini API.
* **The Frontend:** Built completely in vanilla HTML, CSS, and JavaScript. By avoiding heavy frontend frameworks, the app remains incredibly fast and responsive on mobile devices.

## UX & Interface Design
Because this tool is meant to be used on the go with one hand, I prioritized a mobile-first user experience.
* **Intuitive Toggles:** A prominent "Strict Vegetarian" toggle allows users to instantly set their dietary baseline before scanning.
* **Visual Feedback:** Implemented custom CSS animations (a glowing blue scan line) so the user knows the AI is actively processing the image.
* **Clear Hierarchy:** The results are delivered using a traffic-light badge system (Green for Safe, Red for Unsafe) so the user gets an instant verdict without having to read a wall of text.

## The Impact
For the 40% of people managing strict religious diets, ethical choices, or severe food allergies, manual label checking is slow and prone to human error. SafeEats bridges the gap between complex industrial food chemistry and everyday consumer safety.

![image](/images/safeeat2.png)
![image](/images/safeeatimage1.png)