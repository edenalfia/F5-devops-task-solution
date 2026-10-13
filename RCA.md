# Root Cause Analysis

Fill this in as you go. Bullet points are fine — be specific, not long.

---

## Defect 1: Proxy image fails to build

### Symptom / error output
The building of the proxy image failed because the order of the Run and COPY instructions was wrong.

### How I diagnosed it
I looked at the file "proxy/Dockerfile" to see it's content, and noticed that the command "COPY nginx.conf ..." was before the command "RUN apt-get install -y nginx ...".

### Root cause
The docker attempted to copy a configuration file for a service that hadn't been installed yet in the container.

### Fix
I reordered the lines in the file "proxy/Dockerfile". I replaced the places of the RUN command and the COPY command, so that the service will be installed first.

---

## Defect 2: Proxy cannot reach the backend

### Symptom / error output
Requests that were sent through the proxy didn't reach the backend service and returned an error.

### How I diagnosed it
I looked at the file "proxy/nginx.conf" and saw where the proxy was forwarding requests. Then I looked at "docker-compose.yml" and saw that the backend service name didn't match the address in the proxy config.

### Root cause
The proxy was configured to send traffic to "127.0.0.1:8080" and the address 127.0.0.1 refers to the container itself (localhost address), so he tried to send the requests to himself instead of the backend container.

### Fix
I changed the upstream address in "proxy/nginx.conf" from "127.0.0.1:8080" to "backend.8080" so that the Nginx will route the traffic to the backend container according to the Docker's internal network name.

---

## Defect 3: Tests still fail after fixing defect 2

### Symptom / error output

### How I diagnosed it

### Root cause

### Fix, and why I chose it over the alternatives

---

## Defect 4: CI pipeline fails

### Symptom / error output

### How I diagnosed it

### Root cause

### Fix

---

## Bonus questions

Optional. Answer only the ones you got to — number them, skip the rest.

>

---

## Anything you would do differently with more time
