# Python Security Automation: Access Control Management

## Overview
Developed a Python automation script to manage and enforce an IP allow list for a restricted network environment. The goal was to automate the removal of unauthorized IP addresses and improve efficiency in access control operations, transitioning from manual maintenance to a programmable, error-free workflow.

---

## Objective
* **Automate** updates to the internal IP allow list.
* **Remove** unauthorized access entries dynamically.
* **Reduce** manual security administration workload and human error.
* **Improve** accuracy and consistency in access control enforcement.

---

## Approach
The script follows a systematic logic to ensure data integrity during the update process:
1.  **File Access:** Reads authorized IP addresses from `allow_list.txt`.
2.  **Data Transformation:** Converts the raw string data into a list for iterative processing.
3.  **Audit & Filter:** Compares active entries against a predefined `remove_list`.
4.  **Purge:** Removes unauthorized IP addresses with precision.
5.  **Synchronization:** Reconstructs the data and writes the updated list back to the source file.

---

## Python Concepts Leveraged
* **File Handling:** Utilizing `with open()` for secure read/write operations.
* **String Manipulation:** Implementing `.split()` and `.join()` for data parsing.
* **Control Flow:** Using `for` loops and `if` conditional logic for filtering.
* **List Operations:** Managing dynamic data structures with `.remove()`.

---

## Security Impact
* **Strengthens Access Control:** Ensures that only verified IPs retain access to sensitive subnets.
* **Operational Efficiency:** Automates repetitive administrative tasks, allowing the security team to focus on high-level threats.
* **Scalability:** Supports large-scale security operations where manual list updates are no longer feasible.

---

## Full Algorithm Implementation

```python
# Initialization: Define file path and IPs to be removed
import_file = "allow_list.txt"
remove_list = [
    "192.168.97.225", 
    "192.168.158.170", 
    "192.168.201.40", 
    "192.168.58.57"
]

# Step 1: Read the current allow list
with open(import_file, "r") as file:
    ip_addresses = file.read()

# Step 2: Convert string to list for processing
ip_addresses = ip_addresses.split()

# Step 3: Iterate and remove unauthorized IPs
for element in ip_addresses:
    if element in remove_list:
        ip_addresses.remove(element)

# Step 4: Reformat and overwrite the original file
ip_addresses = " ".join(ip_addresses)
with open(import_file, "w") as file:
    file.write(ip_addresses)

# Verification: Display the updated allow list
with open(import_file, "r") as file:
    text = file.read()

print(text)
