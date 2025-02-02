## Automated CVE Exclusion and Vulnerability Reporting in Jenkins Pipeline for Check Point CloudGuard

This comprehensive solution integrates a Python Script into a Jenkins Pipeline to automate CVE exclusion and generate vulnerability reports for Check Point CloudGuard. One script focuses on excluding specific CVEs in CloudGuard, and the other generates detailed reports on vulnerabilities found in images.

### Jenkinsfile Pipeline Integration
- **Jenkins Pipeline Setup**: The provided `Jenkinsfile` automates the execution of the CVE exclusion script in a Jenkins Pipeline.
- **Virtual Environment**: The pipeline sets up a Python virtual environment and installs necessary dependencies (`pandas`, `requests`, `openpyxl`).
- **Parameterized Builds**: Allows specifying the CVE list name, image name, and authorization token as parameters for the build.

### CVE Exclusion Script in Jenkins
- **Automated Process**: Integrated into the Jenkins Pipeline, this script automatically processes and excludes specified CVEs in CloudGuard during `shiftleft image-scan`.
- **Environment ID in ShiftLeft**: The script emphasizes the inclusion of the environment ID for proper policy and environment association in CloudGuard.

### Usage in CloudGuard Image Scans
- **ShiftLeft Command**: The scripts support the `shiftleft image-scan v2` command, which should include the environment ID, e.g., `shiftleft image-scan -i nginx.tar -e <environmentID>`.
- **Report Basis for CVE Exclusions**: The vulnerability report generated is the basis for determining which CVEs to exclude in subsequent CloudGuard image scans.

### Script Functions (Vulnerability Reporting)
- `process_cve`, `process_secret`, `process_threat`: Functions for processing different types of findings and populating the Excel report.
- `main()`: Orchestrates the report generation, including API calls to CloudGuard and Excel file manipulation.

### Requirements and Notes
- **Jenkins Setup**: Requires a Jenkins server with the necessary permissions and environment setup.
- **Script Dependencies**: The scripts rely on external Python libraries and a properly configured CloudGuard API access.
