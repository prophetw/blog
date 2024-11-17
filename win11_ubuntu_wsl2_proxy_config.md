# config host's Proxy
> if wsl2 need to use host's proxy 
> 7890 is proxy port 

```bash
vi ~/.bashrc
vi ~/.zshrc

# if host ip is not changed  
HOST_IP="192.168.1.10"

# 获取宿主机 IP 地址
get_host_ip() {
  ip route | grep default | awk '{print $3}' # use wsl ip recommended method
  # echo "$HOST_IP"  # METHOD use host ip 
}

# 设置代理别名
alias setProxy='export http_proxy="http://$(get_host_ip):7890" && \
export https_proxy="http://$(get_host_ip):7890" && \
export ftp_proxy="http://$(get_host_ip):7890" && \
export all_proxy="socks5://$(get_host_ip):7890" && \
echo "Proxy is enabled Host IP：$(get_host_ip)，port：7890"'

# 关闭代理别名
alias noProxy='unset http_proxy && unset https_proxy && unset ftp_proxy && unset all_proxy && echo "Disable Proxy"'



setProxy # enable Proxy
noProxy  # disable Proxy

```