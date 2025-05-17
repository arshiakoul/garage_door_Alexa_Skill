# garage_door_Alexa_Skill
This Alexa skill is a Python AWS Lambda function that authenticates to the Chamberlain/MyQ API to open, close, and check the status of MyQ-enabled garage doors by voice. It handles LaunchRequest, IntentRequest (MoveIntent, StateIntent), and SessionEndedRequest, using env vars for secure config.
# Alexa Garage Door Opener Skill

A simple Alexa skill (AWS Lambda) in Python that lets you open, close, and check the status of one or more MyQ-enabled garage doors via voice commands.

## Features

- **Open/Close** your garage door by saying “Ask `<invocation name>` to open/close door one (or door two)”.
- **Check Status**: “Ask `<invocation name>` if door one is open” returns “open”, “closed”, or other interim states.
- **Configurable**: All API credentials, invocation name, and skill ID are provided as environment variables.

## Prerequisites

- An Amazon developer account with an Alexa skill configured.
- A Chamberlain/MyQ account and at least one MyQ-enabled garage door opener.
- AWS account with Lambda permissions and ability to set environment variables.
- Python 3.7+ runtime in Lambda.

## Installation

1. **Clone this repo** (or copy the `lambda_function.py` code).  
2. **Deploy** the code to an AWS Lambda function using the Python 3.7+ runtime.  
3. **Link** your Lambda to your Alexa skill’s Endpoint (ARN).

## Configuration

In your Lambda function’s **Environment variables**, set:

| Variable    | Description                                                      |
|-------------|------------------------------------------------------------------|
| `INVONAME`  | Alexa invocation name (e.g., “garage door”)                      |
| `USERNAME`  | Your MyQ account username (email address)                        |
| `PASSWORD`  | Your MyQ account password                                        |
| `SKILL_ID`  | Your Alexa skill’s application ID (starts with `amzn1.ask.skill.`) |
| `APP_ID`    | MyQ API Application ID                                           |
| `HOST_URI`  | (Optional) MyQ host; defaults to `myqexternal.myqdevice.com`     |
| `NO_OPEN`   | Set to `Y` to disable the “open” command (optional)              |

## Usage

- **Open** the door:  
  “Alexa, ask `<invocation name>` door one to open.”
- **Close** the door:  
  “Alexa, ask `<invocation name>` door one to close.”
- **Status** check:  
  “Alexa, ask `<invocation name>` if door one is open.”

## Supported Intents

- `MoveIntent`  
  - Slot `doornum`: `door`, `door 1`, `1`, `door 2`, `2`, etc.  
  - Slot `doorstate`: `open`/`up` or `close`/`down`/`shut`
- `StateIntent`  
  - Slot `doornum`: same as above  
  - Slot `doorstate`: check for `open` vs. `closed`

## Troubleshooting

- Verify your Lambda logs in CloudWatch for any authentication or request errors.
- Ensure the environment variables match exactly (no extra whitespace).
- Confirm that the skill’s Application ID in the Alexa developer console matches `SKILL_ID`.

## Contributing

Feel free to submit issues or pull requests to add features like multi-door support, enhanced error handling, or richer Alexa responses.

## License

This project is released under the MIT License.  

