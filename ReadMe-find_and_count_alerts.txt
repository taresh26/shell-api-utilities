Instructions for Using the Script
Create the Script File: Save the above code in a file named find_and_count_alerts.sh.


nano find_and_count_alerts.sh
Paste the code and save the file.

Make the Script Executable: Run the following command to make the script executable:


chmod +x find_and_count_alerts.sh

Run the Script: You can run the script by providing the log file and an optional search pattern. For example:


./find_and_count_alerts.sh /path/to/logfile.log "search_pattern"
To count and display all errors, warnings, and alerts without filtering, simply omit the search pattern:


./find_and_count_alerts.sh /path/to/logfile.log

Explanation

Argument Handling: The script checks for at least one argument (the log file) and optionally a search pattern.
File Existence Check: It verifies that the specified log file exists.
Finding and Counting Logic: The script uses awk to filter lines based on the search pattern (if provided). It counts occurrences of "ERROR", "WARNING", and "ALERT" in the filtered lines and prints each matching line.
Output: After processing, it displays the total counts for each category.
This script efficiently finds and counts error, warning, and alert messages in your logs while providing visibility into the matching lines!