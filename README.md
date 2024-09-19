# openwrt
https://openwrt.org/

* ifconfig eno1 promisc
*  docker network create -d macvlan --subnet=192.168.0.0/24 --gateway=192.168.0.1 -o parent=eno1 openwrt_net
*  sudo docker run --restart always  --name openwrt  -d --network openwrt_net --privileged shawoo/openwrt /sbin/init
*  docker exec -it openwrt /bin/bash
*  vim /etc/config/network
*  /etc/inti.d/network restart
*  【网络】-【接口】-【物理设置】，将【桥接接口】选项去掉
*  【网络】-【防火墙】-【自定义规则】增加规则：
  <pre>
  iptables -t nat -I POSTROUTING -j MASQUERADE
  </pre>
* PC端修改网关为这个旁路由的地址
