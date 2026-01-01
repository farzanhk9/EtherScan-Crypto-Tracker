# A real-time Ethereum wallet tracker using the Etherscan API.
import requests

def get_wallet_balance(api_key, address):
    url = f"https://api.etherscan.io/api?module=account&action=balance&address={address}&tag=latest&apikey={api_key}"
    
    response = requests.get(url).json()
    if response["status"] == "1":
        # Convert Wei to ETH
        balance_eth = int(response["result"]) / 10**18
        return {"address": address, "balance_eth": balance_eth}
    return {"error": "Invalid API key or address"}

# Usage: Replace with your Etherscan API Key
API_KEY = "YOUR_API_KEY"
WALLET = "0xde0b295669a9fd93d5f28d9ec85e40f4cb697bae"
print(get_wallet_balance(API_KEY, WALLET))

