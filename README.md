# nginx-load-balancer-with-health-check

NGINX build with health-check patches from [yaoweibin's repo](https://github.com/yaoweibin/nginx_upstream_check_module)

### Usage

* Copy services description from **docker-compose.yml** in this repo to your **docker-compose.yml** and as you need.
* Copy local **deployment/nginx.conf** to your volume directory and update **upstream localhost** node.
