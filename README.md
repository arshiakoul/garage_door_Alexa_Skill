# garage_door_Alexa_Skill
This Alexa skill is a Python AWS Lambda function that authenticates to the Chamberlain/MyQ API to open, close, and check the status of MyQ-enabled garage doors by voice. It handles LaunchRequest, IntentRequest (MoveIntent, StateIntent), and SessionEndedRequest, using env vars for secure config.
