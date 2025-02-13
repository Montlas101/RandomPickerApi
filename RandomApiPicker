import random
import requests
from flask import Flask, Response

app = Flask(__name__)

PASTEBIN_URL = "https://pastebin.com/raw/LwfqaCjf"  # Replace with your Pastebin Raw URL
MAX_LENGTH = 400  # Nightbot's character limit


@app.route('/')
def get_random_story():
    try:
        response = requests.get(PASTEBIN_URL)
        if response.status_code == 200:
            lines = response.text.splitlines()
            random_story = random.choice(lines)
            return Response(random_story[:MAX_LENGTH], mimetype="text/plain"
                            )  # Ensures response is under 400 characters
        else:
            return Response("Error: Could not fetch stories",
                            mimetype="text/plain")
    except:
        return Response("Error: Something went wrong", mimetype="text/plain")


if __name__ == "__main__":
    app.run(host="0.0.0.0", port=80)

