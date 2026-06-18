# Federated Learning
---

## General Information and Purpose
- **Service Name/Title:** `federated-learning`
- **Description and purpose:** Enchances the performance of energy consumption predictive models by utilizing the available computation power of IoT devices and keeping private data locally.
- **Owner/Contact Information:** ICCS

---

## Federated Learning Workflow

The federated learning service follows a centralized orchestration approach in which a server coordinates the training process across a fleet of connected IoT devices.

1. **Global Model Distribution**

   * The server maintains the current global forecasting model.
   * Whenever a new global model is available, it is distributed to all connected devices.

2. **Local Training**

   * Each device stores and processes its own energy consumption data locally.
   * Every 15 minutes, devices train the received global model using their most recent local measurements.
   * Raw customer data never leaves the device.

3. **Participant Selection**

   * At predefined intervals, the server selects a subset of available devices to participate in a federated learning round.
   * Selection may be based on device availability, connectivity, or orchestration policies.

4. **Model Aggregation**

   * Selected devices send their updated model parameters to the server.
   * The server performs Federated Averaging (FedAvg) to aggregate the local updates into a new global model.

5. **Global Model Update**

   * The aggregated global model becomes the latest version of the forecasting model.
   * The updated model is then distributed to all connected devices, starting the next training cycle.

### Data Privacy

* Raw energy consumption data remains on the IoT devices.
* Only model parameters and training metadata are exchanged with the server.
* Communication between devices and the server is secured through TLS-enabled MQTT connections.


