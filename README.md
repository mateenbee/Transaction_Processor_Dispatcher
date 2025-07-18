> ⚠️ **Note**: This project is a **template** implementation of a Dispatcher-Performer model using UiPath's REFramework. It serves as a starting point and requires customization to match specific business systems, APIs, data formats, and error-handling needs.

# 📦 Transaction Processor - Dispatcher (UiPath REFramework)

This is the **Dispatcher component** of the Transaction Processor project built using UiPath's **Robotic Enterprise Framework (REFramework)**.

The Dispatcher is responsible for retrieving records from an external CRM system and uploading them as **queue items** into Orchestrator for downstream processing by the Performer bot.

---

## 🚀 Overview

- Fetches data from a CRM via **API calls using SOQL queries**.
- Extracted records are transformed and uploaded to **Orchestrator Queues**.
- Designed to run independently as a scheduled job before the Performer.

---

## 🔧 Features

- Uses the REFramework pattern for scalability and reliability.
- Handles exceptions and retries using built-in mechanisms.
- Communicates with the CRM's **REST API** to pull data.
- Supports dynamic SOQL query customization via Config file.

---

## 📂 Project Structure

Dispatcher/
├── Data/
│ └── Config.xlsx # Contains API details, Queue name, etc.
├── Framework/
│ └── [REFramework files]
├── Process/
│ └── GetTransactionData.xaml # Contains API/CRM logic
├── Main.xaml
└── project.json

---

## 🔑 Configuration

Update the following in `Data/Config.xlsx`:

| Setting Name        | Description                          |
|---------------------|--------------------------------------|
| `QueueName`         | Name of the Orchestrator queue       |
| `CRM_API_Endpoint`  | Base URL for the CRM API             |
| `CRM_SOQL_Query`    | SOQL query used to fetch transactions |
| `Authentication`    | Bearer token or credentials (via assets) |

---

## 🧪 Execution Flow

1. **Initialization**: Loads settings and credentials.
2. **Get Transaction Data**:
   - Sends SOQL query to CRM API.
   - Parses the response and extracts required fields.
3. **Add Queue Items**:
   - Adds each transaction to the defined Orchestrator queue.

---

## 📅 Scheduling

- Recommended to schedule the Dispatcher to run **Once daily before the Performer**.
- Ensures fresh transactions are available for processing.

---

## 📡 External Dependencies

- External CRM system with API access and valid SOQL endpoints.
- Orchestrator queue properly configured.



