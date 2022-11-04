# POSTMORTEM :fire: :fire:

### Issue summary
> An outage occurred at approximately 1700hrs East African Time(EAT) on my ubuntu container and it was keeping it from listening on port 80.
Curl command (curl 0:80) kept giving a connection refused error (curl: (7) Failed to connect to 0 port 80: Connection refused).
#### :worried: :worried:
The expected output is a nginx welcome page.

### Debugging Process :star: :star:
> The debugger (Marcrine) encountered the connection refused error at 17:20 EAT upon testing the connection to nginx server, so she proceeded to 
solving the error using the below steps:
- Checked the nginx configurations.
    Located the sites-enabled folder and navigated to it using the command cd /etc/nginx/sites-enabled.
    The nginx configurations are in the file named default, used command cat default to check the contents of the file.
    She found that nginx was listening on port 8080.

- Changed port 8080 to port 80.
    Edited the nginx configurations located in /etc/nginx/sites-enabled/default file
    by replacing port 8080 with port 80.

- Restarted the nginx service in the ubuntu container.
- Tested the nginx service using the curl command on port 80. Output was as expected.
- Wrote a bash script to automate the error fixing.

### Summary :sunglasses: :fire:
> Always ensure that your nginx configurations are correctly configured depending on your requirements.
Check the port numbers in the configuration file that affect the nginx service.

### Prevention :sparkles: :sparkles:
This error occured due to wrong configurations. To prevent such errors:
- Check service configurations before deployment.
- Confirm port numbers that are in the configuration file.

>Note that I wrote a linux bash script to automate the process if the error ever occurs in the future.
We know that the error won't occur again, we've learnt how to prevent it.
#### :smile: :smile:
