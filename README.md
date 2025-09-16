<<<<<<< HEAD

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



=======
# UrbanGrocers-API-Testing  

## 📌 Overview  
This repository documents **Sprint 4 API testing work** for **Urban Grocers (Kits)** and **Fast Delivery** services.  
The project validates API endpoints using **Postman** with **JSON payloads**, covering both positive and negative scenarios.  

## 🛠 Tools & Technologies  
- **Postman** → API requests & automation  
- **JSON** → request/response format  
- **Google Sheets** → detailed test case management & evidence  
- **HTTP/REST** → API communication  

## ⚙️ Prerequisites  
Before running tests, make sure you have:  
- Installed [Postman](https://www.postman.com/downloads/)  
- Access to UrbanGrocers API base URL (provided by project/environment)  
- Internet connection to access Google Sheets evidence  

> **Note:** Postman exports are not included (`Status: Evidence-only`). You can replicate requests manually using the JSON payloads provided below.  

## 🚀 How to Run Tests  
1. Open **Postman**.  
2. Create a **new request** and configure:  
   - Method: `POST`  
   - URL: (see endpoints below)  
   - Headers:  
     ```
     Content-Type: application/json
     Accept: application/json
     ```  
   - Body: **raw JSON** (see examples).  
3. Send request and validate response:  
   - **Status code** matches expectation (`200`, `400`, `404`).  
   - **Response body** structure and values are correct.  

## 🧪 Coverage Summary  

### Kits API  
**Endpoint:** `POST /api/v1/kits/:id/products`  
- Valid kit ID vs non-existent kit ID → `200 / 404`  
- Product ID validation → reject non-existent IDs → `400`  
- Quantity validation → must be `> 0` and `≤ 30` → `400`  
- JSON structure validation → reject malformed requests → `400`  

### Fast Delivery API  
**Endpoint:** `POST /fast-delivery/v3.1.1/calculate-delivery`  
- Delivery time vs operating hours (boundary tests)  
- Product count and weight limits (positive/negative)  
- Validate response JSON structure and delivery cost calculation  

## 📄 Example Test Cases  

| **ID** | **Test Case Name**                                     | **Endpoint**                               | **Expected**          | **Actual** | **Status** |
|--------|--------------------------------------------------------|--------------------------------------------|-----------------------|------------|------------|
| P001   | Successful delivery calculation with valid data        | `/fast-delivery/v3.1.1/calculate-delivery` | `200 OK` – valid cost | 200 OK     | ✅ PASSED  |
| P002   | Reject non-existent product ID                         | `/api/v1/kits/6/products`                  | `400 Bad Request`     | 200 OK     | ❌ FAILED  |
| P004   | Reject quantity > 30                                   | `/api/v1/kits/6/products`                  | `400 Bad Request`     | 200 OK     | ❌ FAILED  |
| P008   | Reject quantity = 0                                    | `/api/v1/kits/6/products`                  | `400 Bad Request`     | 200 OK     | ❌ FAILED  |
| P010   | Reject kit exceeding total product limit (30 max)      | `/api/v1/kits/6/products`                  | `400 Bad Request`     | 200 OK     | ❌ FAILED  |

👉 Full evidence with detailed steps, payloads, validations, and results is documented in Google Sheets:  
📎 [Sprint 4 Test Cases (JSON)](PUT-YOUR-GOOGLE-SHEET-LINK-HERE)  


## 🧾 Example JSON Payloads  

```md
✅ Valid Delivery Request
{
  "deliveryTime": 10,
  "productsCount": 5,
  "productsWeight": 2.5
}

❌ Invalid Kit Request (non-existent product ID)
{
  "productsList": [
    { "id": 9999, "quantity": 2 }
  ]
}

❌ Invalid Request Structure
{
  "productItems": [
    { "id": 3, "qty": 3 }
  ]
}
