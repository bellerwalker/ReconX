
ReconX: Reconnaissance Tool

Overview:
ReconX is an all-in-one reconnaissance tool designed to gather publicly available information about a target website. 
It leverages multiple techniques to scan and discover open directories, exposed files, subdomains, and other potential vulnerabilities 
on the target site. With features like directory listing, file exposure checks, and subdomain scanning (via Amass), ReconX is a valuable tool 
for penetration testers, ethical hackers, and security researchers.

Key Features:
- Directory Listing Detection: Identifies open directories that are exposed to the public.
- Exposed Configuration Files: Searches for configuration files (like .conf, .ini, .xml, etc.) that may contain sensitive information.
- Exposed Database Files: Scans for database files (e.g., .sql, .mdb, etc.) that are unintentionally exposed.
- Exposed Log Files: Detects publicly accessible log files, which may contain critical user activity or security data.
- Backup and Old Files: Searches for backup files (e.g., .bak, .old, etc.) that may contain important information.
- Install/Setup Files: Detects publicly exposed setup or installation files that can provide insight into system configurations.
- Other Exposed Files (PDF, XLSX, DOCX, etc.): Scans for documents that might contain business or sensitive information.
- Open Redirects: Identifies open redirects that could be exploited for phishing or malicious activities.
- Subdomain Scanner (Amass Integration): Performs subdomain enumeration using the Amass API, with live/dead subdomain status checks.

Installation Requirements:
Before using ReconX, ensure you have the following dependencies installed:

- Python 3.6+: Make sure Python 3.6 or later is installed on your system.
- Required Python Libraries: Install the following Python libraries using pip:
    pip install colorama requests webbrowser amass

- Amass: For subdomain scanning, you’ll need Amass installed on your system. Amass is a powerful subdomain enumeration tool, 
  and it can be installed from the official website or via package managers.
  - On Linux (Debian-based):
      sudo apt install amass
  - On macOS:
      brew install amass
  - For Windows, download and install Amass from its GitHub repository.

How to Use:
1. Run the Script: After installing all dependencies, run the ReconX script by executing it in your terminal or command prompt:
    python reconx.py

2. Select an Option: After launching the tool, you will be prompted with a list of available options. These options allow you to 
   perform specific reconnaissance tasks on the target website.
   Example:
    Pick a Target: example.com
    Pick an option:
    [1] Directory Listing
    [2] Exposed Configuration files
    [3] Exposed Database files
    [4] Exposed log files
    [5] Backup and old files
    [6] Install / Setup files
    [7] Other Files (pdf, xlsx, etc.)
    [8] Open Redirects
    [9] Subdomain Scanner (Amass)

   Type the number corresponding to the option you wish to use (e.g., 1 for Directory Listing).

3. Review the Output: The tool will display the results in your terminal and/or open them in your browser for further exploration.
   For example, for Directory Listing, it will display results like:
    Dork used: site:example.com intitle:"index of"
    [Results shown in browser]

4. Subdomain Scanner (Amass integration): If you select option 9 for Subdomain Scanning, it will use Amass to scan for subdomains 
   associated with the target domain. The status of each subdomain (live or dead) will be displayed.
   Example:
    amass enum -d example.com -o amass_output.txt
    Subdomain scan results:
    live.example.com - HTTP Status: 200 OK
    api.example.com - HTTP Status: 403 Forbidden
    blog.example.com - HTTP Status: 404 Not Found

Example of After Running the Tool:

Scenario: You want to scan a website for exposed configuration files.

1. Run the tool and choose the target (example.com).
2. Select option 2 for Exposed Configuration Files.
3. The tool will search for configuration files like .conf, .ini, or .xml and display the results:
    Dork used: site:example.com filetype:conf | filetype:ini | filetype:xml
    [Results shown in browser]
   It will open a new browser tab with the results, or display them directly in the terminal.

4. For Subdomain Scanning: If you choose option 9, the tool uses Amass to enumerate subdomains, showing which ones are live and which are not:
    amass enum -d example.com -o amass_output.txt
    Subdomain scan results:
    live.example.com - HTTP Status: 200 OK
    api.example.com - HTTP Status: 403 Forbidden

Example Output:

Directory Listing:
    Found open directory: example.com/uploads/
    Found open directory: example.com/files/

Exposed Configuration Files:
    Exposed File: example.com/config/config.xml
    Exposed File: example.com/settings/.env

Subdomain Scanner (Amass):
    Subdomain: api.example.com - HTTP Status: 403 Forbidden
    Subdomain: blog.example.com - HTTP Status: 404 Not Found
    Subdomain: admin.example.com - HTTP Status: 200 OK

ReconX is a comprehensive reconnaissance tool that helps security professionals quickly identify potential vulnerabilities in a target website 
by checking for exposed files, directories, and subdomains. By using powerful features like Amass for subdomain enumeration and various file exposure 
checks, ReconX streamlines the process of collecting critical information for further analysis.
