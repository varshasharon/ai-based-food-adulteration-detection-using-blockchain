#  AI-Based Food Adulteration Detection Using Blockchain

##  Project Overview

Food adulteration and counterfeit products pose serious risks to public health and consumer trust. This project proposes a **secure, intelligent, and transparent food verification system** that combines **Blockchain** for data integrity and **Artificial Intelligence (AI)** for ingredient analysis and personalized health alerts.

Each food product is registered on a blockchain ledger and linked to a **unique QR code**. Consumers can scan the QR code to verify authenticity and receive **AI-driven warnings and recommendations** based on their health conditions and allergies.

##  Objectives

* Ensure **tamper-proof food product authentication**
* Prevent **food adulteration and counterfeit distribution**
* Provide **real-time verification** at the point of purchase
* Deliver **personalized health analysis** based on user allergies and medical conditions
* Improve transparency across the **food supply chain**

---

##  Problem Statement

Current food authentication systems:

* Rely on **centralized databases** vulnerable to tampering
* Lack **real-time verification**
* Do not provide **health-aware ingredient analysis**
* Fail to support consumers with **allergies or chronic conditions**

This project addresses these gaps by integrating **Blockchain + AI** into a consumer-centric solution.


##  Proposed Solution

The system consists of three core modules:

### 1️ Manufacturer Module

* Registers product details (ingredients, batch number, expiry date)
* Stores data securely on the blockchain
* Generates a **unique QR code** for each product

### 2️ Blockchain Network

* Maintains a **decentralized, immutable ledger**
* Prevents data manipulation and unauthorized changes
* Enables transparent auditing and traceability

### 3️ Consumer Application

* Scans QR codes to fetch verified product data
* Uses AI to analyze ingredients
* Compares ingredients with user health profiles
* Displays **warnings, alerts, and recommendations**

---

##  System Architecture

```
Manufacturer → Blockchain Ledger → QR Code
                                   ↓
                           Consumer Application
                                   ↓
                         AI Ingredient Analysis
                                   ↓
                       Health Alerts & Verification
```

---

##  Technologies Used

* **Blockchain** – Secure & decentralized data storage
* **Artificial Intelligence / Machine Learning**
* **QR Code Technology**
* **Python** (AI & logic layer)
* **Web Technologies** (UI)

---

##  Functional Requirements

* Secure product registration
* Blockchain-based data storage
* QR code generation and scanning
* Product authenticity verification
* AI-driven ingredient analysis
* Personalized health alerts

---

##  Non-Functional Requirements

* High accuracy and reliability
* Strong data security and privacy
* Scalable architecture
* User-friendly interface
* Low response time

---

##  Key Features

*  Tamper-proof food records
*  Real-time product verification
*  Allergy & health condition detection
*  Consumer-centric decision support
*  Enhanced trust and transparency

---

##  Future Enhancements

* Image-based adulteration detection
* IoT-enabled supply chain tracking
* Integration with government food safety authorities
* Mobile app deployment
* Advanced AI recommendation engine

---
## Code
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract FoodAuthentication {

    // Structure to store product details
    struct Product {
        string productName;
        string ingredients;
        string manufacturer;
        uint256 manufacturingDate;
        bool exists;
    }

    // Mapping product ID to Product
    mapping(string => Product) private products;

    // Event for product registration
    event ProductRegistered(
        string productId,
        string productName,
        string manufacturer
    );

    // Register a new food product
    function registerProduct(
        string memory _productId,
        string memory _productName,
        string memory _ingredients,
        string memory _manufacturer,
        uint256 _manufacturingDate
    ) public {
        require(!products[_productId].exists, "Product already registered");

        products[_productId] = Product(
            _productName,
            _ingredients,
            _manufacturer,
            _manufacturingDate,
            true
        );

        emit ProductRegistered(_productId, _productName, _manufacturer);
    }

    // Verify and fetch product details
    function verifyProduct(string memory _productId)
        public
        view
        returns (
            string memory,
            string memory,
            string memory,
            uint256
        )
    {
        require(products[_productId].exists, "Product not found");

        Product memory product = products[_productId];
        return (
            product.productName,
            product.ingredients,
            product.manufacturer,
            product.manufacturingDate
        );
    }

    // Check if product exists
    function isProductAuthentic(string memory _productId)
        public
        view
        returns (bool)
    {
        return products[_productId].exists;
    }
}


```

##  Applications

* Food safety verification
* Health-aware food consumption
* Supply chain transparency
* Regulatory auditing support
* Consumer awareness platforms

---

## Sample Output

<img width="1919" height="824" alt="Screenshot 2026-02-01 184504" src="https://github.com/user-attachments/assets/23665280-a056-4bb5-901b-28f6f11c771a" />
<img width="1392" height="680" alt="Screenshot 2026-02-01 184651" src="https://github.com/user-attachments/assets/964e0b09-c834-4223-baf1-7e85b0e73cec" />
<img width="1919" height="830" alt="Screenshot 2026-02-01 184633" src="https://github.com/user-attachments/assets/31c81120-4f5e-4a8a-9444-3755d920ab55" />


##  References

* Tian et al., *Blockchain-Based Food Traceability*, IEEE
* Kamilaris et al., *Blockchain in Food Supply Chains*, Elsevier
* Zhang et al., *AI in Food Safety*, Journal of Food Engineering
* Nakamoto, *Bitcoin Whitepaper*

---

