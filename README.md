## CVE Exclusion Automation for Check Point CloudGuard Integration

This Python script is designed to streamline the process of excluding specific Common Vulnerabilities and Exposures (CVEs) in Check Point CloudGuard. It primarily focuses on adding CVEs into a dictionary in CloudGuard, which are then automatically excluded during the execution of the `shiftleft` command. The script also emphasizes the need to include the environment ID in the `shiftleft` command, linking the policy with the shiftleft environment.

### Purpose and Integration
- **Targeted Use Case**: The script is tailored for managing CVE exclusions in Check Point CloudGuard's shiftleft image scans.
- **Integration with ShiftLeft Command**: It facilitates the exclusion of specific CVEs during the `shiftleft image-scan` process, enhancing security measures.

### Key Features
1. **Automated CVE Exclusion**: Dynamically adds CVEs to a CloudGuard dictionary for automatic exclusion.
2. **Integration with CloudGuard API**: Utilizes CloudGuard's API to manage the CVE exclusion list.
3. **ShiftLeft Command Compatibility**: Designed to support the `shiftleft image-scan v2` command, including the necessary environment ID parameter.

### Usage in the Context of Check Point CloudGuard
1. **Initial Configuration**: Set environment variables for CVE list name, image name, and authentication token.
2. **Excel Input**: Reads CVEs from an Excel file (`imagereport.xlsx`), identifying which CVEs to exclude based on specified criteria.
3. **CloudGuard List Management**: Creates or updates a list of CVEs in CloudGuard, handling list deletion and creation as needed.

### Example ShiftLeft Command
```
shiftleft image-scan -i nginx.tar -e <environmentID>
```
This command includes the environment ID (`-e`) parameter, which is critical for associating the scan with the correct policy and environment in CloudGuard.

### Script Functions
- `get_entity_id(image_name, auth_header)`: Retrieves entity ID from CloudGuard using the image name.
- `chunk_cve_list(cve_list, size=15)`: Breaks the CVE list into manageable chunks for processing.
- `main()`: Main function orchestrating the script logic, from reading the Excel file to updating the CloudGuard list.

### Requirements and Notes
- Ensure that the Python environment has the necessary packages (`pandas`, `requests`) installed.
- The script assumes the presence of an Excel file with specific columns for processing.
- It's crucial to handle authentication tokens securely and maintain proper environment variable configurations.

---

This readme provides a detailed overview of the script's functionality, purpose, and integration with Check Point CloudGuard, specifically highlighting its role in enhancing the security measures during the image scan process.
