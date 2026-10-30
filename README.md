# Tericsoft DevOps Task
A static Hello World page served by nginx:alpine in a Docker container on port 8081.
Deployed on AWS EC2 and on ECS Fargate.

```bash
git clone https://github.com/tech-dipesh/Tericsoft_oa.git && cd Tericsoft_oa
docker build -t tericsoft . && docker run -d --name tericsoft -p 8081:8081 tericsoft
```

Open http://localhost:8081 to see the page.
Files: Dockerfile, nginx.conf, app/index.html.
- Publiic Url is: `http://3.7.66.83:8081/`

## Problem:
I. SSH Connection HUng: My security group allowed port 22 only from an old IP address, so SSH attempts hung instead of failing cleanly. Which the Once i Updated a Inbound Rule with my current ip with the connection.

II. SSM agent not connecting: Which the AWS Systems Manager showed `TargetNotConnected` for the instance. The SSM agent was not running With I started it after SSH access was restored.
III. Port 8081 reachable locally but not publicly:  After running the nginx container, `localhost:8081` returned the page but the public IP kept loading. With I've Tested out a Container which was a healthy but the 8081 is not opened in the security group. Which the Custom TCP Rule For the Universal IP: `0.0.0.0/0` With the Public URL Worked.
IV. ECS Fargate task blocked by default security group:  For the ECS bonus, the task definition and service were created successfully and the task showed `Running`, which i check the public ip is becoming a still hung. The Task is inherteed on the default security group. Which teach me the ECS which don't inherit EC@ Instance Security Group.
## Cost Cleanup:
After recording, I deleted the ECS service, cluster, and ECR repository, and terminated the EC2 instance to avoid ongoing charges.

## Video Link:
https://drive.google.com/file/d/1VhMBDnHpvRCTTV8TXH8RPixD7lwNso3Y/view
# Thanks.