# Access log and auditing

Seafile offers administrators following tools to monitor the system:

* access.log: under directory `logs/stats-logs`
* login log: in the web interface
* traffic log: in the web interface 
* public link list: in the web interface

## access.log

access.log (under directory logs/stats-logs) records the following information

* file download via web
* file download via API

The format is:

    date, operation type, user, ip, web agent, library_id, library_name, file path. 

Exmaple:

    2014-09-15 14:11:42,679 - file-download-web jye@163.com 127.0.0.1 "Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/35.0.1916.153 Safari/537.36" 82ae9775-bd0f-4fec-b35c-b64c63fc4938 "api" "/pack.md"

    2014-09-15 14:16:31,798 - file-download-api jye@163.com 127.0.0.1 "curl/7.27.0" dfe1aa6a-9948-4c4c-9bf2-e67b2913199a "gc" "/unp.txt"

