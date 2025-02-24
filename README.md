
# OCPP 1.6 Chargebox Simulator

A simple chargepoint simulator, working with OCPP 1.6.

Based on the old simpler version of the [OCPP-J-CP-Simulator](https://github.com/nenecmrf/OCPP-J-CP-Simulator).

## Features

- Define the central station to connect with
- Specify the tag ID that will activate the chargebox
- Send chargebox message events:
  - Connect
  - Authorize
  - Start/Stop transaction
  - Heartbeat
  - Meter values
  - Status Notification
  - Data Transfer
- Response commands implemented:
  - GetConfiguration
  - ChangeConfiguration
  - RemoteStartTransaction

## Getting Started

### Prerequisites

- A web browser (e.g., Chrome, Firefox)
- Internet connection

### Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/pondsan1412/OCPP-1.6-Chargebox-Simulator.git
    ```
2. Navigate to the project directory:
    ```sh
    cd OCPP-1.6-Chargebox-Simulator
    ```

### Usage

1. Open the simulator.html file in your web browser.
2. Enter the Central Station ID and Tag ID.
3. Use the buttons to simulate various chargebox actions.

### Screenshots

![Simulator UI](https://github.com/user-attachments/assets/2b9bf226-22a8-4d91-92b7-dbcbf83cd2fe)

## Changes Made

- Improved UI for a more modern and professional look.
- Updated the `startTransaction` and `stopTransaction` functions for better functionality.
- Added indicators to show the status of the connection and transactions.
- Enhanced the logging mechanism to provide better feedback in the console.

### Updated Functions

#### startTransaction

```javascript
function startTransaction(idTag, connectorId) {
    sessionStorage.setItem('LastAction', "startTransaction");
    $('.indicator').hide();
    $('#green').show();
    connector_locked = true;
    logMsg("Connector status changed to: " + connector_locked);

    let payload = {
        "connectorId": connectorId,
        "idTag": idTag,
        "timestamp": formatDate(new Date()),
        "meterStart": 0,
        "reservationId": 0
    };

    console.log("StartTransaction Payload: ", payload);

    let strtT = JSON.stringify([2, id, "StartTransaction", payload]);
    _websocket.send(strtT);
}
```

#### stopTransaction

```javascript
function stopTransaction(idTag, transactionId) {
    sessionStorage.setItem('LastAction', "stopTransaction");
    $('.indicator').hide();
    connector_locked = false;
    logMsg("Connector status changed to: " + connector_locked);
    $('#yellow').show();

    const payload = {
        transactionId: Number(transactionId),
        idTag: idTag,
        transactionData: [
            {
                sampledValue: [
                    {
                        context: "Interruption.Begin",
                        format: "Raw",
                        location: "Body",
                        measurand: "Energy.Active.Import.Register",
                        phase: "L1",
                        unit: "Wh",
                        value: "100"
                    }
                ],
                timestamp: formatDate(new Date())
            }
        ],
        timestamp: formatDate(new Date()),
        meterStop: 20
    };

    console.log("StopTransaction Payload:", payload);
    const stpT = JSON.stringify([2, id, "StopTransaction", payload]);
    _websocket.send(stpT);
}
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [OCPP-J-CP-Simulator](https://github.com/nenecmrf/OCPP-J-CP-Simulator)
- [Font Awesome](https://fontawesome.com/)
- [jQuery](https://jquery.com/)
