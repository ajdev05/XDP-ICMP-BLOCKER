# Block ICMP with XDP
## A program that blocks ICMP requests using eBPF and XDP on the kernel level.


## You will need to download all of the dependencies for eBPF for your Linux OS

## After you have everything that you need


## RUN

```
apt update -y ; apt upgrade -y
apt install git
git clone git@github.com:ajdev05/xdp_block_icmp.git
cd xdp_block_icmp
```

## Compile
```
clang -Wall -O2 -target bpf -c icmp_blocker.c -o icmp_blocker.o
```



## Hook the program up to the NIC
