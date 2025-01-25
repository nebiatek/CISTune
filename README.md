# CISTune

CISTune is a PowerShell module designed to help administrators deploy the CIS Critical Security Controls (v8) using Microsoft Intune. The module allows you to choose from three Implementation Groups (IG1, IG2, IG3) to ensure your environment meets the desired level of security controls.

## Features

- Deploy CIS v8 controls via PowerShell scripts.
- Select specific Implementation Group (IG1, IG2, IG3).
- Easily extensible and configurable.

## Installation

To install the CISTune module, follow these steps:

1. Clone the repository:
    ```powershell
    git clone https://github.com/nebiatek/CISTune.git
    ```

2. Navigate to the repository directory:
    ```powershell
    cd CISTune
    ```

3. Import the module:
    ```powershell
    Import-Module .\src\CISTune.psm1
    ```

## Usage

### Deploy Controls

To deploy controls for a specific Implementation Group, use the following commands:

#### Complete Implementation Group
```powershell
# Example to deploy all IG1 controls
Deploy-CISTune -ImplementationGroup 1

# Example to deploy all IG1 + IG2 controls
Deploy-CISTune -ImplementationGroup 2

# Example to deploy all IG1 + IG 2 + IG3 controls
Deploy-CISTune -ImplementationGroup 3
```

#### Implementation Group with exclusions
```powershell
# Example to deploy all IG1 safeguard except all those from control group 3
Deploy-CISTune -ImplementationGroup 1 -ExcludeControlGroup 3

# Example to deploy all IG1 + IG2 safeguard except safeguard 8 from group 3
Deploy-CISTune -ImplementationGroup 1 -ExcludeSafeguard "3.8"

# Example to deploy all IG1 + IG2 safeguard except multiple safeguards
Deploy-CISTune -ImplementationGroup 1 -ExcludeSafeguard @("3.8","4.7","4.9")
```