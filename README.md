# Phishing Detection API

## Introduction
Phishing is a common and dangerous form of cyberattack where attackers deceive victims into revealing sensitive information by masquerading as a trustworthy entity. The growing sophistication of phishing tactics has made it critical for organizations and individuals to adopt proactive measures against these threats.

This project implements a machine learning-based solution to detect phishing URLs. By analyzing various characteristics of URLs, the system can predict whether a given URL is likely to be legitimate or a phishing attempt. The solution is designed to be easily integrated as a RESTful API, making it a valuable tool for real-time phishing detection.

## How the Project Detects Phishing
The core of this project is a machine learning model trained to differentiate between legitimate and phishing URLs based on a set of 30 features extracted from the URLs. These features include characteristics like URL length, the presence of special characters, SSL status, domain age, and more. By examining these attributes, the model learns to identify patterns and behaviors that are common in phishing attempts.
### Key Features for Spotting Phishing

The first step to building a phishing detection system is understanding what makes a URL or email suspicious.

While the design is made quite similar to the legitimate site , we focus on quantitative features:

 1. **having_IP_Address:** URLs that contain an IP address instead of a domain name are often suspicious.
 2. **URL_Length:** Longer URLs can indicate attempts to obfuscate the true destination of a link.
 3. **Shortening_Service:** Shortened URLs can hide malicious addresses, making them harder to detect.
 4. **having_At_Symbol:** The presence of "@" in a URL can be used to trick users into visiting malicious sites.
 5. **double_slash_redirecting:** Redirections following "//" can sometimes be a sign of phishing.
 6. **Prefix_Suffix:** A hyphen ("-") in a domain name might indicate a fake version of a legitimate site.
 7. **having_Sub_Domain:** More subdomains may indicate attempts to imitate a legitimate site.
 8. **SSLfinal_State:** Valid SSL certificates are common on legitimate sites; phishing sites often don't have them.
 9. **Domain_registeration_length:** Short registration periods can indicate temporary, fraudulent use.
 10. **Favicon:** Using a different favicon or loading it from an external source can be suspicious.
 11. **port:** Legitimate sites generally use standard ports; unusual ports might be suspect.
 12. **HTTPS_token:** Some phishing sites include "https" in their domain names to appear legitimate.
 13. **Request_URL:** Checking if elements (like images) are hosted on external sites can detect phishing.
 14. **URL_of_Anchor:** Phishing sites often use anchor tags with misleading URLs.
 15. **Links_in_tags:** Similar to "Request_URL", but checks meta, script, and link tags for malicious links.
 16. **SFH (Server Form Handler):** If form data is sent to a different domain, it may indicate phishing.
 17. **Submitting_to_email:** Forms that use "mailto:" can indicate phishing attempts.
 18. **Abnormal_URL:** A URL structure that deviates from the norm could be suspicious.
 19. **Redirect:** Phishing websites often use multiple redirects to disguise the final destination.
 20. **on_mouseover:** Changing behavior (e.g., the status bar) on hover can be a phishing tactic.
 21. **RightClick:** Disabling right-click can prevent users from inspecting or copying the link.
 22. **popUpWidnow:** Pop-up windows can be used to trick users into entering personal information.
 23. **Iframe:** Hidden iframes can indicate attempts to mask malicious content.
 24. **age_of_domain:** Newer domains are more likely to be used for phishing.
 25. **DNSRecord:** Phishing sites may lack valid DNS records or have mismatched information.
 26. **web_traffic:** Lower traffic suggests a site could be less trustworthy.
 27. **Page_Rank:** Sites with low PageRank may be less legitimate.
 28. **Google_Index:** Phishing sites might not be indexed by Google, indicating a lack of legitimacy.
 29. **Links_pointing_to_page:** Phishing sites might have few backlinks or external links.
 30. **Statistical_report:** Utilizing databases of known phishing sites can help in detection.

These features give us clues about whether a URL or email is safe. Now, let's see how we can teach an AI to use these clues.
### The Dataset and its preprocessing:
The dataset contains 102816 web hits and 30 features were recorded for each of the hit. Also, a class value has been given for each of the record.
### Building Our AI: Different Approaches

The following machine learning algorithms were used and evaluated:
1. **Logistic Regression**
2. **Decision Tree Regressor**
3. **Random Forest Classifier**
4. **Support Vector Machine (SVM)**

After experimenting with these models, the **Random Forest Classifier** was found to be the most accurate, achieving a precision and recall of 96.7% and an accuracy of 97%.

The project also includes a RESTful API built using Flask, allowing users to input a URL and receive a prediction on whether the URL is safe or potentially malicious.

## The project contains two pages:

HomePage:
 The home page introduces the aimof the project  and  allows users to input a URL.

![image](https://github.com/user-attachments/assets/3135dd5b-2ce7-4344-869b-0f279fb2b739)
ResultPage:
The result page gives the output as a spam or not spam url:

![image](https://github.com/user-attachments/assets/c61a6a69-38b5-489d-878a-b11e3b166f85)

## How to run the project:

Frontend with react.js:

npm start.

Backend with Flask:

### Create a virtual environment and activate it.

python -m venv venv.

source venv/bin/activate.

### Install the dependencies using pip install -r requirements.txt.

pip install -r requirements.txt.

### Run python app.py to start the Flask server.

python app.py.
