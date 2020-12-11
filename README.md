# OCPP-1.6-Chargebox-Simulator
A simple chargepoint simulator, working with OCPP 1.6

Based on the old simpler version of the [OCPP-J-CP-Simulator](https://github.com/nenecmrf/OCPP-J-CP-Simulator)

Functionalities:
- Define the central station to connect with
- Specify the tag id that will activate the chargebox
- Send chargebox message events:
  - Connect
  - Authorize
  - Start/Stop transaction
  - Heartbeat
  - Meter values
  - Status Notification
  - Data Transfer
 
- Response command implemented
  - GetConfiguration
  - ChangeConfiguration
  - RemoteStartTransaction
