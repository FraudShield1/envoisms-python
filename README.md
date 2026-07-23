# EnvoiSMS Python SDK

Official Python SDK for [EnvoiSMS.ma](https://envoisms.ma) — SMS, WhatsApp & OTP API platform for Morocco.

For full API documentation and specifications, visit [EnvoiSMS Documentation](https://envoisms.ma/fr/docs).

## Installation

```bash
pip install envoisms
```

## Quick Start

```python
import os
from envoisms import EnvoiSMSClient

client = EnvoiSMSClient(api_key=os.getenv("ENVOISMS_API_KEY"))

# Send SMS
response = client.send(
    to="+212600000000",
    message="Votre code de vérification est 492018",
    from_sender="MonBusiness"
)

print(f"Message ID: {response['id']}")
```

## OTP Verification

```python
# 1. Send OTP
otp_res = client.send_otp(
    to="+212600000000",
    brand="MonBusiness",
    code_length=6,
    expiry=600
)

session_id = otp_res["session_id"]

# 2. Verify User Code
check_res = client.check_otp(
    session_id=session_id,
    code="492018"
)

if check_res.get("verified"):
    print("OTP code is valid!")
```

## Documentation

Comprehensive API guide: [https://envoisms.ma/fr/docs](https://envoisms.ma/fr/docs).

## License

MIT
