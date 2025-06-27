大陆白名单路由规则

ip段信息取自 [misakaio](https://github.com/misakaio/chnroutes2)
由Github Action自动构建于此。

策略路由分流的实现方法：

**CN.rsc** 是往Firewall - address lists 里生ip段列表。
```
/file remove [find name="CNip.rsc"]
/tool fetch url="https://cdn.jsdelivr.net/gh/GitHubd3b7c/chnroute/blob/main/CN.rsc"
:if ([:len [/file find name=CNip.rsc]] > 0) do={
/ip firewall address-list remove [find comment="AS4809"]
/import CN.rsc
}
```

用于Firewall - mangle页，通过dst-addrss= 引用

comment 名称仅作为 ROS 脚本引用，无任何实际意义可根据需要自行更改
