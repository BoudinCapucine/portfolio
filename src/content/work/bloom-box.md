---
title: AI-Powered Mission-Consultant Matching System
publishDate: 2019-12-01 00:00:00
img: /assets/avisia.jpg
img_alt: A bright pink sheet of paper used to wrap flowers curves in front of rich blue background
description: |
  We paired with a cutting-edge music API and a team of horticulturalists
  to build AI-generated playlists that maximize houseplant health.
tags:
  - BigQuery
  - GCP
  - Dataiku
---

### Objective 
My internship at a data science consulting firm, aligned perfectly with my academic studies. I aimed to develop an application to match available missions with in-house consultants using advanced data processing and machine learning.
I focused on creating the model that employed search and matching algorithms. Utilizing tools like Dataiku and Google Cloud Platform (GCP), including BigQuery, the project aimed to enhance the matching experience between tenders and consultants. 
Key objectives included:

- Streamlining the sales team's process for matching consultants to missions.
- Allowing consultants to find similar profiles for potential mission changes.

### Implementation Process
The application featured a search bar enabling users to submit tenders or search by keywords. I distinguished between two main functions:

- Searching: Finding a consultant or mission based on text, a short description, or a keyword.

![Texte alternatif](/assets/plot26.jpg "Searching")

- Matching: Associating consultants with similar profiles.

![Texte alternatif](/assets/plot27.jpg "Matching")

### Challenges and Solutions
I conducted research to identify the best algorithms and implemented them:

- Developed a keyword extraction method using BERT.
- Created embeddings for consultant and mission attributes.
- Used cosine distance for similarity calculations.
- I realized that not all attributes were necessary, leading to a refined selection focusing on skills and mission details (summaries and keywords).
By testing various keyword extraction methods, I found TF-IDF to be the most effective for improving matching accuracy.

### First Improvement: Grouping Skills by Category
Following suggested improvements, I identified the need to consolidate similar skills in the dataset. For instance, "SQL" and "Database Management" are closely related but created discrepancies in matching missions and consultants. To address this, I aimed to group subcategories of skills, allowing for better alignment.

With access to an OpenAI API key, I planned to use prompts to aggregate skills into families. By providing OpenAI with all skills in my dataset, I aimed to categorize them effectively. 

### Second Improvement: Adding Stopwords to TF-IDF
Using keywords with the TF-IDF method proved effective for matching missions and consultants. However, I noticed many irrelevant terms, such as pronouns and conjunctions, cluttering the results. This issue arose primarily with shorter texts where the algorithm included too many words.

I proposed limiting the number of keywords based on text length but was advised against it due to potential information loss. Instead, my mentor suggested utilizing a "stop words" list to exclude non-essential terms. I compiled a refined list of around 100 common words to enhance the relevance of generated keywords.

### Third Improvement: Replacing BERT with OpenAI

While BERT performed well, we identified several compelling reasons to switch to OpenAI's model for enhanced capabilities:

- Improved Performance: OpenAI's model is more advanced and offers better handling of complex language tasks, which could lead to more accurate summaries and enhanced overall performance.

- Flexibility in Summarization: Using Dataiku's built-in text summarization feature presented challenges with prompt constraints, often resulting in excessively lengthy summaries with irrelevant details. OpenAI's capabilities allow for more precise control over output length and content.

### Automation
To ensure daily updates, I automated the processing scripts. The application required the creation of tables in BigQuery, followed by data processing in Dataiku, and similarity calculations in GCP. I structured the flow in Dataiku to streamline this process, enabling automatic updates each morning at 4 AM before office hours.

### Results
By combining my processed data, embeddings, and similarity calculations with the front end, users can search for consultants or missions by entering keywords or text in a search bar.

![Texte alternatif](/assets/projet_avisia.jpg "Result")