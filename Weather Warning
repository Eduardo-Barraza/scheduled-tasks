import requests
import json
import os
from twilio.rest import Client

API_KEY = os.environ.get("API_KEY")

url = "https://api.openweathermap.org/data/2.5/forecast"

response = requests.get(url, params={
    "lat": 39.953388,
    "lon": -74.198,
    "appid": API_KEY,
    "cnt": 5,
})

print(response.status_code)
response.raise_for_status()
APIdata = response.json()

will_rain = False
for hour_code in APIdata["list"]:
    condition_code = hour_code["weather"][0]["id"]
    if int(condition_code) < 700:
        will_rain = True
if will_rain:

        account_sid = os.environ.get("account_sid")
        auth_token = os.environ.get("auth_token")
        client = Client(account_sid, auth_token)

        message = client.messages.create(
            from_='whatsapp:+14155238886',
            body='Bring an umbrella',
            to='whatsapp:+12015393721'
        )


