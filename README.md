# Block ICMP with XDP
## A program that blocks ICMP requests using eBPF and XDP on the kernel level.


## You will need to download all of the dependencies for eBPF for your OS, my preference is Ubuntu 20.04.
```
sudo apt install clang llvm libelf-dev libpcap-dev gcc-multilib build-essential
sudo apt install linux-tools-$(uname -r)
sudo apt install linux-headers-$(uname -r)
sudo apt install linux-tools-common linux-tools-generic
sudo apt install libbpf-dev
```

## After you have everything that you need


## RUN

```
apt update -y ; apt upgrade -y
apt install git
git clone https://github.com/ajdev05/XDP-ICMP-BLOCKER.git
cd XDP-ICMP-BLOCKER
```

## Compile
```
clang -Wall -O2 -target bpf -c icmp_blocker.c -o icmp_blocker.o
```



## Hook the program up to the NIC

*EG : sudo ip link set dev [interface name] xdp obj icmp_blocker.o sec xdp_icmp_blocker*

```
sudo ip link set dev eth0 xdp obj icmp_blocker.o sec xdp_icmp_blocker
```

## Un-attach or stop the program from the NIC

*EG: sudo ip link set dev [interface] xdp off*
```
sudo ip link set dev eth0 xdp off
```
