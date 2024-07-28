# BMDC API by zenjahid
<p align="center"><img src="https://socialify.git.ci/zenjahid/BMDC-API/image?description=1&font=Source%20Code%20Pro&forks=1&issues=1&language=1&name=1&owner=1&pattern=Solid&pulls=1&stargazers=1&theme=Dark" alt="TeleDoc" width="640" height="320" /></p>

## Description

This repository provides documentation and example usage of the BMDC API, which allows users to authenticate doctors with their registration numbers.

## Table of Contents
- [Overview](#overview)
- [API Endpoints](#api-endpoints)
  - [Version 1](#version-1)
    - [Get Captcha](#get-captcha)
    - [Get Doctor Info](#get-doctor-info)
  - [Version 2](#version-2)
    - [Get Doctor Info with Autocomplete Captcha](#get-doctor-info-with-autocomplete-captcha)

## Overview

The BMDC API enables users to authenticate doctors using their registration numbers. This API has been developed by zenjahid and includes two versions with different functionalities.

## API Endpoints

### Version 1

#### Get Captcha

**Request Type:** GET

**Request URL:**
```bash
https://bmdc-api.onrender.com/v1/get_captcha
```

**Parameters:** None

**Response:**
```json
{
    "error": "no",
    "captcha_src": "https://verify.bmdc.org.bd/cpt/1720618813.933.jpg",
    "csrf_token_value": "a0b94f6fe222d26aa95d6a2cd0ff6e2d",
    "action_key_value": "vWb5HoQ6YwhR",
    "cookies": {
        "bmdckyc_csrf_cookie": "a0b94f6fe222d26aa95d6a2cd0ff6e2d"
    }
}
```

**Error Response:**

```json

{
    "error": "yes"
}
```

#### Get Doctor Info
**Request Type:** POST

**Request URL:**

```bash
https://bmdc-api.onrender.com/v1/get_info
```
**Parameters (as JSON):**

```json
{
    "bmdckyc_csrf_token": "xxx",
    "reg_ful_no": "xxx",
    "captcha_code": "xxx",
    "action_key": "xxx",
    "cookies": "xxx"
}
```
Response:

```json
{
    "error": "no",
    "reg_no": "A-123321",
    "name": "TANBIM SHIFAT - E - ALAM PROVA",
    "father_name": "MD. SAIFUL ALAM",
    "mother_name": "JESSY ALAM",
    "dob": "**/**/1998",
    "blood": "B+",
    "reg_year": "2023",
    "reg_valid": "07/06/2028",
    "reg_stat": "ACTIVE"
}
```

Error Response:

```json
{
    "error": "yes"
}
```

### Version 2
#### Get Doctor Info with Autocomplete Captcha
Request Type: POST

Request URL:

```bash
https://bmdc-api.onrender.com/v2/get_data
```
Parameters (as JSON):

```json
{
    "reg_no": 122431,
    "try_time": 12 // optional, the default value is set to 10; just reg_no is fine. If having trouble with not getting a response, increase its value.
}
```

Response:
```json
{
    "error": "no",
    "reg_no": "A-123321",
    "name": "TANBIM SHIFAT - E - ALAM PROVA",
    "father_name": "MD. SAIFUL ALAM",
    "mother_name": "JESSY ALAM",
    "dob": "**/**/1998",
    "blood": "B+",
    "reg_year": "2023",
    "reg_valid": "07/06/2028",
    "reg_stat": "ACTIVE"
}
```
Error Response:

```json
{
    "error": "yes"
}
```
