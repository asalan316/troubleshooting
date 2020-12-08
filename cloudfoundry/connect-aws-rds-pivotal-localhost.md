# asds

# Access AWS RDS available in Pivotal Cloud Foundry from Developer IDE 

Sometimes developers wants to access cloud database from their developer machines. 

 -  Find database hostname, username and password from VCAP_SERVICES enviornment variable
  
    ```mermaid
    $ cf env APP-A
    Getting env variables for app APP-A in org XXXX / space dev as abc@cfapps.io...
    OK

    System-Provided:
    {
    "VCAP_SERVICES": {
    "aws-rds-mysql": [
    {
        "binding_name": null,
        "credentials": {
        "database": "my_74459f56f5cc4",
        "engine": "mysql",
        "engine_version": "5.7.26",
        "hostname": "xxxxxxxxxxxxxxxxxxxxxxxxxxx.rds.amazonaws.com",
        "password": "xxxxxxxxxxxxxxxxxxxxxxxx",
        "port": 3306,
        "uri": "mysql://<username>:<password>@xxxxxxxxxxxxxxxxxxxxxxxxxxx.rds.amazonaws.com:3306/my_74459f56f5cc4",
        "username": "<username>"
        },
        ....
   
  -  SSH to your app from your terminal 
    
        `cf ssh -L 63306:xxxxxxxxxxxxxxxxxxxxxxxxxxx.rds.amazonaws.com:3306 YOUR_APP_NAME`

        - hostname = xxxxxxxxxxxxxxxxxxxxxxxxxxx.rds.amazonaws.com (from VCAP_SERVICES environment variable)
        - YOUR_APP_NAME = Name of the app which is connected to the databse. In this example, APP-A


Once you have created the tunnel, you can access the AWS-RDS database from your localhost on port 63306

- install DB Navigator plugin in intellj (Community Edition), if you have't installed already -> https://plugins.jetbrains.com/plugin/1800-database-navigator

- Connect to AWS RDS -> notice the connection is made via localhost on port 63306
  
![Connection Dettails in DB Navigator](https://github.com/asalan316/troubleshooting/blob/master/cloudfoundry/db-navigator-connection-setting.png?raw=true)

References:
- https://docs.pivotal.io/pivotalcf/2-4/devguide/deploy-apps/ssh-services.html


