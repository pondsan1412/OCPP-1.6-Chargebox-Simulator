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
    git clone https://github.com/yourusername/OCPP-1.6-Chargebox-Simulator.git
    ```
2. Navigate to the project directory:
    ```sh
    cd OCPP-1.6-Chargebox-Simulator
    ```

### Usage

1. Open the [simulator.html](http://_vscodecontentref_/0) file in your web browser.
2. Enter the Central Station ID and Tag ID.
3. Use the buttons to simulate various chargebox actions.

### Screenshots

![image](https://github.com/user-attachments/assets/2b9bf226-22a8-4d91-92b7-dbcbf83cd2fe)


## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [OCPP-J-CP-Simulator](https://github.com/nenecmrf/OCPP-J-CP-Simulator)
- [Font Awesome](https://fontawesome.com/)
- [jQuery](https://jquery.com/)
