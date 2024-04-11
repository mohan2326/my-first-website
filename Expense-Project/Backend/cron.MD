Create a script:

Create a script file, for example, start_services.sh, and add the following content:


#!/bin/bash
# Start MySQL
systemctl start mysqld
# Start backend service
systemctl start backend

Save the file and make it executable:
chmod +x start_services.sh

Edit cron jobs:
Open the cron tab editor:
crontab -e
Add a line to execute your script upon system reboot:
@reboot /path/to/start_services.sh
Replace /path/to/start_services.sh with the actual path to your script file.

Save and exit:

Save your changes and exit the editor.

Now, whenever your system restarts, the start_services.sh script will be executed, which will start both the MySQL and backend services.
