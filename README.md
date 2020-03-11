# Monitoring for 3rd Demo

In our case all monitoring is set while deploying infrastructure. You can view how it's work more detailed in [this](https://github.com/sxVova/ansible-deploy) and [this](https://github.com/sxVova/ansible-roles) repos. README for each monitoring role and it's usage is located in the appropriate directory. If you want to parse this process in more detail, read the next paragraph.

## ACTIONS FOR MANUAL MONITORING SETUP

1. Install stackdriver-agent to the VMs with sentry and gitlab.
2. Add ports-forwarding of the services that we'll go to monitor to the docker-compose.yml of the sentry-vm, so we can see 'em from localhost.
3. Edit gitlab.rb of the gitlab-vm so that the services we need work on tcp (by default: on unix sockets) and was visible from localhost. Also for nginx monitoring on the gitlab-vm, we need to enable metrics gathering in the same gitlab.rb.
   In our case, we use the [correct gitlab.rb](https://github.com/sxVova/ansible-roles/blob/master/roles/gitlab_role/templates/gitlab.rb.j2) when deploying gitlab.
4. Set postgres user & db in the postgres-container of the sentry-vm for monitoring.
5. Set nginx monitoring [plugin](https://cloud.google.com/monitoring/agent/plugins/nginx) to the sentry-vm.
   For gitlab-vm almost the same, but change port in nginx.conf in previous guide on 9999.
6. Set redis monitoring [plugin](https://cloud.google.com/monitoring/agent/plugins/redis) to the sentry-vm and gitlab-vm.
7. Set memcached monitoring [plugin]( https://cloud.google.com/monitoring/agent/plugins/memcached) to the sentry-vm.
8. Set zookeeper monitoring [plugin](https://cloud.google.com/monitoring/agent/plugins/zookeeper) to the sentry-vm.
9. Set postgres monitoring [plugin]( https://cloud.google.com/monitoring/agent/plugins/postgres) to the sentry-vm.

## Authors

https://github.com/nrthrn-orc & https://github.com/sxVova



