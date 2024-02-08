# Direct Line API for copilot in Power Apps

Power Apps has a chatbot control that allows you to easily add your own custom copilot (built with copilot studio) to your app. However, at this time, this component does not allow you to programmetically interact with the copilot, so you cannot pass predefined messages or get the latest response to use for further processing. This demo component shows an alternative that allows you to do this.

<img width="1275" alt="image" src="https://github.com/BoelenJ/directline-copilot-powerapps/assets/117845677/7f0c4b14-fa3a-41ae-a795-8f7b69deea68">


## Implementation

To achieve more flexibility, this solution uses the Direct Line API 3.0, which allows you to communicate with your bot via REST [Direct Line 3.0 API](https://learn.microsoft.com/en-us/azure/bot-service/rest-api/bot-framework-rest-direct-line-3-0-api-reference?view=azure-bot-service-4.0). This API allows for manually polling new messages and for using websockets, to keep the implementation in Power Apps as low-code as possible, manual polling is implemented with a timer control, but using websockets is a feasible alternative when using PCF controls.

## Setup
To test this setup, you can import the solution into your power apps environment. The solution contains a canvas app with a demo implementation and a custom connector for the Direct Line API. After importing, you should create a connection for this API as follows:
- In copilot studio, select the copilot you want to add to the app.
- Select settings -> security -> web channel security.
- Copy one of the secrets.
- Create a new connection in power apps for the custom connector, as authorization, you should add: "Bearer {value from the previous step}"

