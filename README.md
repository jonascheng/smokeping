# Customized SmokePing

[aws/us-east-1](https://sping.jonasc.dev)

## Usage

```console
$ docker run --rm --name smokeping \
  -e TZ=Asia/Taipei \
  -e PUID=1001 \
  -e PGID=1001 \ 
  -p 80:80 \
  -v `pwd`/data:/data \
  --restart unless-stopped \
  linuxserver/smokeping
```

## Parameters

Container images are configured using parameters passed at runtime (such as those above). 
These parameters are separated by a colon and indicate <external>:<internal> respectively. 
For example, -p 80:80 would expose port 80 from inside the container to be accessible from the host's IP on port 80 outside the container.

| Parameter | Function |
| :----: | --- |
| `-p 80` | Allows HTTP access to the internal webserver. |
| `-e PUID=1001` | for UserID - see below for explanation |
| `-e PGID=1001` | for GroupID - see below for explanation |
| `-e TZ=Asia/Taipei` | Specify a timezone to use EG Europe/London |
| `-v /config` | Configure the `Targets` file here |
| `-v /data` | Storage location for db and application data (graphs etc) |

## User / Group Identifiers

When using volumes (-v flags) permissions issues can arise between the host OS and the container, we avoid this issue by allowing you to specify the user PUID and group PGID.
Ensure any volume directories on the host are owned by the same user you specify and any permissions issues will vanish like magic.
In this instance PUID=1001 and PGID=1001, to find yours use id user as below:

```
$ id username
  uid=1001(dockeruser) gid=1001(dockergroup) groups=1001(dockergroup)
```

## Targets

* Facebook
* Youtube
* JupiterBroadcasting
* GoogleSearch
* linuxserverio

## References

* [Using Amazon EFS to Persist Data from Amazon ECS Containers](https://github.com/awslabs/amazon-ecs-amazon-efs)
* [Tutorial: Continuous Deployment with CodePipeline](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs-cd-pipeline.html)
