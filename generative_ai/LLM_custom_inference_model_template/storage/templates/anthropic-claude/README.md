# Anthropic Model Wrapper 

This code folder provides a wrapper for any OpenAI model so that your prompts and responses are monitored and governend by DataRobot. 

For DataRobot 10.2, this wrapper is fully compliant with the OpenAI client Specification. So just simply swap your endpoint and you gain access to all of DataRobot's monitoring, evaluations and guardrails. You can use any Anthropic model by changin the model parameter on the chat input. 

## Testing Locally

You can test this wrapper locally using drum. 

First install the requirements file in new virtual environment:

```
python -m pip venv venv
source venv/bin/activate
pip install -r requirements.txt
```


Now you can run drum server

```
export TARGET_NAME=resultText
export ANTHROPIC_API_KEY=<YOUR ANTHROPIC KEY>
drum server -cd . --target-type textgeneration --address localhost:6789
```

You can test the wrapper by running the test script

```
curl http://localhost:6789/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "claude-3-sonnet-20240229",
    "messages": [
      {
        "role": "system",
        "content": "You are a helpful assistant."
      },
      {
        "role": "user",
        "content": "Hello!"
      }
    ]
  }'

```


