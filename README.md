
**Status:** Evidence-only (Postman exports unavailable)  
This repository documents Sprint 4 API testing work for **Urban Grocers (Kits)** and **Fast Delivery**, using **JSON** payloads.

---

## 🧪 Coverage Summary

### Kits API
- **Endpoint:** `POST /api/v1/kits/:id/products`
- **Test Scenarios:**
  - Valid kit ID vs non-existent kit ID → 200 / 404
  - Product ID validation: non-existent products → 400
  - `productsList` length ≤ 30 and JSON structure validation

### Fast Delivery API
- **Endpoint:** `POST /fast-delivery/v3.1.1/calculate-delivery`
- **Test Scenarios:**
  - `deliveryTime` vs operating hours (boundary tests)
  - `productsCount` and `productsWeight` limits (positive/negative)
  - Validate response JSON structure and values

---

## 📄 Test Evidence
- All test cases executed using **JSON payloads**.
- Positive and negative scenarios covered.
- Detailed test cases, execution results, and status documented in Google Sheets:  
[📎 Sprint 4 Test Cases (JSON)](https://docs.google.com/spreadsheets/d/1EIoT3fpPra5E0-Ac9f7rUX0_qLcpxwEIY0Y8g8NbtMI/edit?usp=share_link)

---

## 🛠 Tools & Technologies

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![JSON](https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white)
![API Testing](https://img.shields.io/badge/API%20Testing-007ACC?style=for-the-badge)
![HTTP](https://img.shields.io/badge/HTTP-009688?style=for-the-badge)
![Automation](https://img.shields.io/badge/Automation-4CAF50?style=for-the-badge)

---

## 📌 Test Execution Approach

1. **Send Request:** Use Postman with JSON payloads.  
2. **Verify Status Code:** Check that response code matches expected (200, 400, 404).  
3. **Validate Response Body:** Confirm JSON structure and values are correct.  
4. **Error Handling:**  
   - Timeout, network issues, or server down → log and mark `Blocked`.  
   - Unexpected 200 OK → log as defect and mark `Failed`.

---

## ✅ Notes
- JSON format adopted instead of previous XML for all API requests.  
- Covers **functional, positive, and negative test scenarios**.  
- Test results are fully documented and accessible via the linked Google Sheet.

## 📄 Test Evidence
- All test cases executed using **JSON payloads**.
- Positive and negative scenarios covered.
- Detailed test cases, execution results, and status documented in Google Sheets:  
[📎 Sprint 4 Test Cases (JSON)](https://docs.google.com/spreadsheets/d/1EIoT3fpPra5E0-Ac9f7rUX0_qLcpxwEIY0Y8g8NbtMI/edit?usp=share_link)




