---
sidebar_position: 0
---

# Get started

Monitoring is a way to automatically check if a service, like a website or app, is working. If the service stops working (downtime), monitoring notices the problem and tells the right person on the development team.

## Creating first monitor 

We'll set up a monitor to check our website. It will regularly look for a "success" message. If it doesn't find this message, it will alert us.

This "success" message is called an HTTP status code (2XX). The monitor checks for this code every few seconds. If the website doesn't show this code, the monitor tells the person currently in charge. If they don't respond, the whole team gets alerted.

### Step 1: Enter monitor name, URL na frequency

- Go to Monitors > Add monitor
- Enter monitor name, website/app URL and choose check frequency

![Screen](/img/monitors-default.png)

### Step 2: Users & alerts
Select who can view this monitor and how they'll be notified if an incident happens.

![Screen](/img/monitors-users.png)

### Step 3: Creat monitor

- After completing the basic setup, click on **Create monitor**.
- The monitor is now active, regularly checking the URL.




