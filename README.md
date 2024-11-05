# REFrameWork Template

### **Robotic Enterprise Framework**

- Built on top of the *Transactional Business Process* template
- Uses a *State Machine* layout for the phases of the automation project
- Offers high-level logging, exception handling, and recovery
- Keeps external settings in the `Config.xlsx` file and Orchestrator assets
- Retrieves credentials from Orchestrator assets and the *Windows Credential Manager*
- Fetches transaction data from a DataRow (configured in the `Config.xlsx` file) instead of an Orchestrator queue
- Updates transaction status based on the processing outcome (Success, Business Rule Exception, System Exception)
- Takes screenshots in case of system exceptions

---

## How It Works

### 1. **INITIALIZE PROCESS**
- `./Framework/InitiAllSettings` - Load configuration data from the `Config.xlsx` file and external assets
- `./Framework/GetAppCredential` - Retrieve credentials from Orchestrator assets or Windows Credential Manager
- `./Framework/InitiAllApplications` - Open and log in to applications used throughout the process

### 2. **GET TRANSACTION DATA**
- `./Framework/GetTransactionData` - Fetches transaction data from a DataRow 
  - The DataRow is loaded based on the data source specified in the `Config.xlsx` file.
  - Each transaction can be processed sequentially from the DataTable or DataRow retrieved.

### 3. **PROCESS TRANSACTION**
- `Process` - Process the transaction and invoke any other workflows related to the process being automated.
- `./Framework/SetTransactionStatus` - Updates the status of the processed transaction (Success, Business Rule Exception, or System Exception).

### 4. **END PROCESS**
- `./Framework/CloseAllApplications` - Logs out and closes the applications used throughout the process.

---

## For New Project

### 1. **Config.xlsx Setup**
- Check the `Config.xlsx` file and add or customize any required fields and values.
- Ensure that the field for the transaction data source (previously 
