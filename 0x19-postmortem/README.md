Postmortem

Issue Summary:

Duration: , 20 July 2023, 10:00 AM to May 24, 2023, 12:30 PM (UTC) Impact: The web service hosted on web-01 experienced an outage, resulting in slow or no access for users. Approximately 90% of users were affected by the service disruption.

Timeline:

10:00 AM: I detected the issue when checking the status of nginx server and the alert indicated servers not running on web-01 and web-02.

Actions taken: I immediately investigated the issue by checking the system logs and network connections. Initially, I assumed that a software misconfiguration or a network issue might have caused the problem.

Misleading investigation paths:

I focused on checking the software configurations and network connectivity on web-01, which consumed valuable time without identifying the root cause.

10:30 AM: As the issue persisted, I escalated the incident to the network engineering team and peers for further analysis and assistance.

11:00 AM: The network engineering team identified a wrong routing configuration on web-01, with Public Key error and leading to service disruption.

Actions taken: Together with the network engineering team, I reconfigured the routing on web-01 to ensure proper traffic flow.

To check log files:

1- Config file ----> /etc/ssh/ssh_config
2- -File /etc/nginx/nginx.conf
3- DEBUGGING NGINX --       ps auxf | grep nginx - to view

May 24, 2023,

11:00 PM: Generated and new ssh-keys - updated Public key in Server and local files,

Created a log-in script for the 2 servers web-01 and web-02 similar to load balancer lb-01.
With the routing fixed, the web service started to recover, and users gradually regained access.

12:30 PM: I officially resolved the incident as the web service was fully operational again.


Root Cause and Resolution:

Root Cause: 

The root cause of the web stack outage was a misconfigured routing on web-01 but was not on  web-02. On setting up web-02 a new ssh-key was generated creating a new public key. Therefore on log-in created authentication conflicts resulting in a service disruption.

Resolution: I fixed the issue by correcting the routing configuration on web-01 to be similar to web-02 by adding a Load balancer lb-01 to handle requests.
. Working closely with the network engineering team, I reviewed the routing tables and reconfigured them to ensure proper traffic flow. After the fix, traffic was correctly directed, and the web service was able to serve users as expected.

Corrective and Preventative Measures: To prevent similar incidents in the future and improve system reliability, I will implement the following measures:

Strengthen monitoring: Enhance our monitoring capabilities to detect  and configure server uptime and downtime.

Setting up a script to and manage Password and authentication - therefore disable Password auth.
This will involve setting up alerts and utilizing monitoring tools to provide real-time insights into the network infrastructure.

Conduct regular configuration audits: Implement regular audits of network configurations to identify any misconfigurations or discrepancies that might impact the system's performance. I will leverage automated configuration management tools to ensure consistency and correctness.

Enable firewalls: Implement proper firewall rules and access controls to restrict unauthorized traffic and protect against potential security threats.

Provide incident response training: Conduct training sessions for the team members on effective incident response procedures, including proper investigation techniques and escalation paths.

Perform a post-incident review: Conduct a thorough review of the incident, including the initial misleading investigation paths, to identify areas for improvement and refine our incident response process.

Tasks to Address the Issue:
Update Authentication scripts for web-01 and web-02 to the same configurations as well as lb-01.

Enable firewalls: Configure and enable firewalls on the network infrastructure to enhance security and prevent unauthorized access.

Enhance monitoring system: Set up alerts and monitoring tools to detect routing anomalies and latency issues in real time.

Conduct incident response training: Organize training sessions for the team to improve incident response capabilities and ensure effective troubleshooting.

Perform post-incident review: Schedule a post-incident review to analyze the incident in detail, identify areas for improvement, and implement necessary changes based on the findings.

By implementing these measures and addressing the specific tasks, I aim to enhance the reliability and resilience of my web servers.
