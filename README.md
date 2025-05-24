# BMDC Doctor Verification API

A FastAPI-based service to verify MBBS/BDS doctor registration details from the Bangladesh Medical & Dental Council (BMDC) website.

## 🌐 API Endpoint
```
https://bmdc-api-vercel.vercel.app/
```

## ✨ Features
- Fetch registration details for MBBS/BDS doctors
- Automatic captcha solving using AI
- Simple JSON response format
- Asynchronous processing for better performance
- Built with FastAPI for high performance

## 🚀 Usage

### Base Endpoint
```http
GET /
```
Returns basic API information.

### Doctor Data Endpoint
```http
POST /doc_data
```

#### 📥 Request Parameters (JSON Body)
| Parameter    | Type   | Required | Default | Description                              |
|--------------|--------|----------|---------|------------------------------------------|
| `reg_no`     | int    | Yes      | -       | 6-digit registration number              |
| `reg_type`   | int    | No       | 1       | 1 for MBBS, 2 for BDS                    |
| `timeout_sec`| int    | No       | 10      | Timeout in seconds for the request       |

#### 📤 Response Format
**Successful Response:**
```json
{
  "error": "false",
  "info_type": "MBBS Doctor",
  "reg_no": "A-123321",
  "name": "DOCTOR NAME",
  "father_name": "FATHER'S NAME",
  "mother_name": "MOTHER'S NAME",
  "dob": "**/**/1998",
  "blood": "B+",
  "reg_year": "2023",
  "reg_valid": "07/06/2028",
  "reg_stat": "ACTIVE"
}
```

**Error Responses:**
```json
{
  "error": "true",
  "error_details": "Error message here"
}
```

#### 📋 Example Requests

**cURL:**
```bash
curl -X POST "https://bmdc-api-vercel.vercel.app/doc_data" \
-H "Content-Type: application/json" \
-d '{"reg_no": 123456}'
```

**Python:**
```python
import requests

url = "https://bmdc-api-vercel.vercel.app/doc_data"
payload = {
    "reg_no": 123456,
    "reg_type": 1,
    "timeout_sec": 15
}

response = requests.post(url, json=payload)
print(response.json())
```

**JavaScript:**
```javascript
fetch('https://bmdc-api-vercel.vercel.app/doc_data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    reg_no: 123456,
    reg_type: 1
  }),
})
.then(response => response.json())
.then(data => console.log(data));
```

## ⚖️ Legal Disclaimer
1. This project solely uses **publicly accessible** information provided by the Bangladesh Medical & Dental Council (BMDC) through their official verification portal at [verify.bmdc.org.bd](https://verify.bmdc.org.bd)

2. All data accessed by this API is already publicly available to anyone through BMDC's official website

3. This project does not:
   - Store or cache any personal data
   - Modify or alter original data in any way
   - Bypass any paywalls or authentication systems
   - Access non-public or restricted information

4. The API simply provides a programmatic interface to access information that is already openly available through manual search on BMDC's website

5. Users of this API are responsible for complying with all applicable laws and regulations regarding data usage

## 🛠️ Error Handling
Common error responses include:
- `Register number must be 6 digits`
- `No valid registration found with this information!`
- `Failed to fetch data within timeout`
- `Invalid Captcha Code!` (automatically retried by the API)

## ⚠️ Limitations
- Requires internet connection
- Dependent on BMDC website availability
- May fail if BMDC changes their website structure


## 👨‍💻 Author
[@zenjahid](https://zenjahid.com) - For support or questions, please contact the developer.

---

*Note: This API is not officially affiliated with BMDC. Use at your own discretion.*
