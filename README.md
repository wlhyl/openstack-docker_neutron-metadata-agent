# 环境变量
- RABBIT_HOST: rabbitmq IP
- RABBIT_USERID: rabbitmq user
- RABBIT_PASSWORD: rabbitmq user 的 password
- KEYSTONE_INTERNAL_ENDPOINT: keystone internal endpoint
- KEYSTONE_ADMIN_ENDPOINT: keystone admin endpoint
- NEUTRON_PASS: openstack neutron密码
- NOVA_METADATA_IP: nova internal endpoint
- AUTH_REGION: RegionOne

# volumes:
- /etc/neutron/: /etc/neutron

# 启动neutron-metadata-agent
```bash
docker run -d --name neutron-metadata-agent \
    -v /opt/openstack/neutron-plugin-openvswitch-agent/:/etc/neutron \
    -v /opt/openstack/log/neutron-plugin-openvswitch-agent/:/var/log/neutron/ \
    -e RABBIT_HOST=10.64.0.52 \
    -e RABBIT_USERID=openstack \
    -e RABBIT_PASSWORD=openstack \
    -e KEYSTONE_INTERNAL_ENDPOINT=10.64.0.52 \
    -e KEYSTONE_ADMIN_ENDPOINT=10.64.0.52 \
    -e NEUTRON_PASS=neutron_pass \
    -e NOVA_METADATA_IP=10.64.0.52 \
    -e AUTH_REGION=RegionOne \
    10.64.0.50:5000/lzh/neutron-metadata-agent:kilo
```