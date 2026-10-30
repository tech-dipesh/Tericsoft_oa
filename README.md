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
# Thanks.