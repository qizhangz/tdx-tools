## TDX Measurement Tool

The measurement tool runs within TD guest to get RTMR value from TDREPORT via
Linux attestion driver, and gets the full TD event log from CCEL ACPI table.
Then it uses the TD event log to verify the RTMR value or change.

CSP or tenant developer could use it to analyze and debug the TDX measurement
before providing the TDX guest VM.

![](https://github.com/intel/tdx-tools/blob/main/doc/tdx_measurement.png)

### Prerequisites

The Log Area Start Address (LASA) is from ACPI CCEL table. Please see [GHCI specification](https://cdrdv2.intel.com/v1/dl/getContent/726790).

### Run

1. Get Event Log

    ```
    ./tdx_eventlogs
    ```

    The example output for the event log in [grub boot](https://github.com/intel/tdx-tools/blob/main/doc/measure_log_grub_boot.txt)
    and [direct boot](https://github.com/intel/tdx-tools/blob/main/doc/measure_log_direct_boot.txt)

2. Get TD Report

    ```
    ./tdx_tdreport
    ```

3. Verify the RTMR

    ```
    ./tdx_verify_rtmr
    ```

### Installation

Build and install TDX Measurement Tool:

```sh
python3 setup.py bdist_wheel
pip3 install dist/*.whl --force-reinstall
```
